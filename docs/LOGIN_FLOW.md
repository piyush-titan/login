# Login / Sign-up flow (Mia)

![Login flow](login-flow.png)

## The flow, step by step

**1. Mobile number screen**
- If **Remember me** saved a number in this browser, it is pre-filled. Otherwise the field is empty.
- Consent boxes are **always unticked**. Nothing is remembered or fetched.
- Remember me is ticked by default.
- No block or account check happens here (privacy). Every valid number goes to the OTP screen.

**2. OTP screen**
- 6 digits, valid 5 min. Resend after 30 s, max 3 resends. 5 attempts.
- 5 wrong codes → number blocked for 24 h. The block and countdown show **only here**.

**3a. Existing customer** → consent ticked on screen 1 is sent (only if something was ticked) → *Welcome back*.

**3b. New customer** → *Create account* (Zoya adds Title) → account created with screen 1 consent → *Your account is ready*.

**4. Email already used by another account**
- *Sign in with ••••• 3469* → OTP to that number → signed in to the existing account.
- *Use this email for my new account* → OTP to the email → new account created, email moves to it.
- *Use a different email* → back to Create account.

**5. After any successful sign-in**
- Remember me ticked → save **only the mobile number** in this browser.
- Unticked → remove the saved number if it was this one.

## Every scenario

| # | Scenario | What the customer sees | Where it ends | Screen switcher |
|---|---|---|---|---|
| 1 | First visit, nothing saved | Empty number field, boxes unticked | Screen 1 | `phone` |
| 2 | Came back, Remember me was on | Number pre-filled, boxes unticked | Screen 1 | `phone-remembered` |
| 3 | Incognito / new device / new browser | Same as first visit | Screen 1 | `phone` |
| 4 | Number too short, wrong start, empty | Inline error under field | Stays on Screen 1 | `phone-invalid` |
| 5 | Marketing ticked, no channel | “Choose at least one way…” error | Stays on Screen 1 | — |
| 6 | Server down / offline | Network error banner | Stays on Screen 1 | `phone-network` |
| 7 | Correct OTP, existing customer | Welcome back | Signed in | `success-returning` |
| 8 | Correct OTP, new customer | Create account form | Screen 3 | `details` |
| 9 | Fewer than 6 digits | “Enter all 6 digits” | Stays on OTP | `otp-incomplete` |
| 10 | Wrong code (1–4) | “That code isn’t right. N attempts left.” | Stays on OTP | `otp-wrong` |
| 11 | 5th wrong code | Blocked, 24 h countdown, input disabled | OTP (blocked) | `otp-blocked` |
| 12 | Blocked number tries again later | Goes to OTP screen, sees remaining time | OTP (blocked) | `otp-blocked` |
| 13 | Code older than 5 min | “This code has expired. Tap Resend.” | Stays on OTP | `otp-expired` |
| 14 | Waiting to resend | “Resend in 0:30” timer | Stays on OTP | `otp` |
| 15 | Resend available / sent | “Resend code” / “A new code is on its way” | Stays on OTP | `otp-resend`, `otp-resent` |
| 16 | All 3 resends used | “You’ve used all 3 resends.” | Stays on OTP | `otp-max-resends` |
| 17 | Back from OTP | Number and ticks kept | Screen 1 | — |
| 18 | Create account – missing / bad fields | Inline errors | Stays on Screen 3 | `details-errors` |
| 19 | Email typo (gmial.com) | “Did you mean gmail.com?” | Stays on Screen 3 | `details-typo` |
| 20 | Email free | Your account is ready | Signed in | `success-new` |
| 21 | Email used by another account | Choice screen | Screen 4 | `swap` |
| 22 | → Sign in with other number | OTP to that number | Signed in (existing) | `otp-alt` |
| 23 | → Use this email for new account | OTP to email | Account ready, email moved | `otp-email`, `success-swapped` |
| 24 | → Use a different email | Back to form | Screen 3 | — |
| 25 | Close (×) at any step | Pop-up closes, nothing saved or sent | — | — |
| 26 | Log out | Session ends; saved number stays (if Remember me) | — | — |

## When consent is sent
- Only **after OTP succeeds**, never before.
- Existing customer: sent only if at least one box is ticked.
- New customer: sent with account creation.
- Nothing is ever read back or pre-ticked. Opt-out is via the external link.

## Mermaid source
```mermaid
flowchart TD
  A([Customer taps Login]) --> B{Number saved by<br/>Remember me in<br/>this browser?}
  B -- Yes --> C1[Screen 1 · Mobile number<br/>number pre-filled]
  B -- No --> C2[Screen 1 · Mobile number<br/>empty]
  C1 --> D[Customer enters or edits number<br/>ticks consent boxes if they want<br/>all boxes start unticked<br/>Remember me ticked by default]
  C2 --> D
  D --> E{Number valid?<br/>10 digits, starts 6-9}
  E -- No --> E1[/Inline error under the field/] --> D
  E -- Yes --> E2{Marketing ticked but<br/>no channel chosen?}
  E2 -- Yes --> E3[/Error: choose at least one way<br/>or untick marketing/] --> D
  E2 -- No --> F[Tap Get OTP]
  F --> F1{Server reachable?}
  F1 -- No --> F2[/Network error, stay on Screen 1/] --> D
  F1 -- Yes --> G{Number blocked?<br/>5 wrong codes<br/>in last 24 h}
  G -- Yes --> G1[OTP screen · Blocked<br/>countdown up to 24:00:00<br/>code box disabled]
  G1 -. Back .-> D
  G -- No --> H[Screen 2 · Enter OTP<br/>6 digits, valid 5 min<br/>Resend after 30 s, max 3]
  H --> I{Code check}
  I -- Fewer than 6 digits --> I1[/Enter all 6 digits/] --> H
  I -- Expired --> I2[/Code expired, tap Resend/] --> H
  I -- Wrong, attempts left --> I3[/That code isn't right · N attempts left/] --> H
  I -- 5th wrong code --> G1
  I -- Correct --> J{Account exists<br/>for this number?}
  H -. Back .-> D

  J -- Yes --> K[Send consent ticked on Screen 1<br/>only if something was ticked]
  K --> S1([Welcome back · signed in])

  J -- No --> L[Screen 3 · Create account<br/>Title Zoya only, first name,<br/>last name, email]
  L --> L1{Fields valid?}
  L1 -- No --> L2[/Inline errors or email typo suggestion/] --> L
  L1 -- Yes --> M{Email already used by<br/>another account?}
  M -- No --> N[Create account + send consent<br/>from Screen 1]
  N --> S2([Your account is ready])
  M -- Yes --> P[Screen 4 · Email linked to<br/>another account]
  P -- Use a different email --> L
  P -- Sign in with the other number --> Q[OTP to that number<br/>same OTP rules]
  Q --> S3([Signed in to the existing account])
  P -- Use this email for new account --> R[OTP to the email<br/>same OTP rules]
  R --> R1[Create account, email moves<br/>to it + send consent]
  R1 --> S4([Your account is ready])

  S1 --> Z{Remember me ticked?}
  S2 --> Z
  S3 --> Z
  S4 --> Z
  Z -- Yes --> Z1[Save only the mobile number<br/>in this browser]
  Z -- No --> Z2[Remove the saved number<br/>if it was this one]

  classDef start fill:#FBE9EC,stroke:#D14A61,color:#3a3a3a
  classDef screen fill:#ffffff,stroke:#D14A61,color:#3a3a3a
  classDef decision fill:#F5F5F5,stroke:#9a9a9a,color:#3a3a3a
  classDef err fill:#FFF4F5,stroke:#E39AA7,color:#7a3a46
  classDef ok fill:#EEF7F0,stroke:#7DB38A,color:#2f5a3a
  classDef block fill:#FFF4F5,stroke:#D14A61,color:#7a3a46,stroke-width:2px
  class A start
  class C1,C2,D,F,H,L,P,Q,R,K,N,R1,Z1,Z2 screen
  class B,E,E2,F1,G,I,J,L1,M,Z decision
  class E1,E3,F2,I1,I2,I3,L2 err
  class S1,S2,S3,S4 ok
  class G1 block
```
