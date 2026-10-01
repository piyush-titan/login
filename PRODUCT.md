# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Plain HTML/CSS/JS prototype (framework-free) so it ports cleanly to the live Salesforce Commerce Cloud (ISML) storefront.

## Users

Shoppers on miabytanishq.com, mostly on mobile, who have tapped "Login" or hit an auth gate (wishlist, cart, checkout) mid-browse. They want back into shopping fast. They include returning customers and first-time customers. Some arrive already having a Tata Neu identity.

## Product Purpose

A unified, OTP-based Sign In / Sign Up for Mia by Tanishq (a Titan / Tata brand) that also captures explicit, granular marketing and personalisation consent. Success means more registrations, fewer auth failures, clean consent records, and customers returned to the page they were on.

## Positioning

A single phone-first flow where the system, not the user, decides between sign in and sign up (via Tata Neu lookup). Consent is granular and unbundled from account creation.

## Operating Context

- Rendered as a modal or sheet over any storefront page. After success the user stays on that page and sees a "Continue Shopping" confirmation that links to the All Jewellery PLP.
- OTP is issued via the existing Tata Neu mechanism. New registrations are sent to Tata Neu and to Salesforce Service Cloud as a Lead.
- Email swap: if the entered email belongs to another mobile number, the user either continues with the existing account (OTP to the masked old mobile, selected by default) or moves the email to the new number (OTP to the email).
- The country-code dropdown keeps the same country list as the existing site.

## Capabilities and Constraints

- Sign-in steps: mobile number, then OTP ("Verify & Continue"), then a success popup. States: invalid mobile, incorrect OTP (stay on screen and retry), and OTP expired (Resend appears only after expiry).
- Sign-up steps: mobile, then OTP, then profile. First Name is mandatory and alphabets only. Last Name is optional per the latest Figma note and alphabets only. Email is mandatory and must be a valid format.
- Inputs must accept only characters relevant to each field.
- Consent copy (verbatim):
  - "I would like to receive marketing communications from Titan and its businesses about its products, services, offers, and special occasion promotions."
  - "Please select how you would like to hear from us:" with Email, WhatsApp, Call and Text Messages as checkboxes.
  - "I consent to the use of my personal data to provide personalized recommendations, offers, and experiences based on my preferences and interactions." (checkbox)
  - "By continuing, I acknowledge the Privacy Notice and agree to the Terms & Conditions"
- Links:
  - Privacy Notice: https://www.miabytanishq.com/en_IN/privacy-notice.html
  - Terms & Conditions: https://www.miabytanishq.com/en_IN/content/privacy-policy?cid=tnc&category=termsandconditionsdata
- Consent display rules (decided by the user):
  - All consent given: returning visits show preferences collapsed (summary + "Edit").
  - Partial consent: also collapsed.
  - No consent at all: always show the full block expanded, every time.
- Canonical flow: mobile number → OTP → existing user signed in / new user → name + email → if email belongs to another account, email swap screen ("This email is already registered with another mobile number") with two options: "Verify <email>" (email OTP, then the email is moved to the new account and the user is signed in) or "Continue with *******3469" (default; plain OTP login on the original number).
- New users see consent expanded and unticked on the details step. Returning users see it after OTP (never before verification, to avoid leaking preferences), on the success view, under the rules above.

## Brand Commitments

- Mia by Tanishq. Primary colour #D14A61. Supporting colours: white and greys only. No dark colours anywhere (no dark backgrounds or dark surfaces).
- The current storefront uses a serif display face for headings and a humanist sans for UI. The logo is a pink script "Mia by Tanishq" mark.

## Evidence on Hand

- `Login_Flow.docx`: user stories and acceptance criteria. It was written for the Zoya variant of the same journey and is being reused for Mia.
- The live site's login modal (screenshots in `.playwright-mcp/`). It currently shows a "Sign In/Up for ₹500 Off" first-purchase offer.
- No Figma access. Do not invent offers, figures or legal text beyond the above.

## Product Principles

1. Phone first, one decision per screen. The system works out whether this is sign in or sign up.
2. Consent is explicit, granular, unticked by default and never a condition of creating an account.
3. Every error explains how to fix it and keeps the user's input.
4. Return the shopper to where they were.

## Accessibility & Inclusion

WCAG 2.2 AA. Full keyboard and screen-reader support for OTP and checkboxes, 44px touch targets, SMS OTP autofill (`autocomplete="one-time-code"`), and legible contrast even with the light-only palette.
