# Privacy Policy — NoteVpro ABA

**Last updated:** April 2026  
**Version:** 1.0

---

## 1. Who We Are

NoteVpro ABA, a product of VSoftware Solutions LLC ("we", "our", "the extension") is a Chrome browser extension designed to assist
Applied Behavior Analysis (ABA) therapists in reviewing clinical session notes for compliance
with BACB standards, CPT billing codes, and payer requirements.

---

## 2. What Data We Handle

### 2.1 Clinical Note Text

When you initiate a note review, the extension reads the text content of the session note
currently open in your EHR system. This text may contain Protected Health Information (PHI)
as defined under HIPAA.

**Before any data leaves your browser**, the extension automatically anonymizes the note:

- Patient names → replaced with `[CLIENT]`
- Therapist names → replaced with `[THERAPIST]`
- Dates of birth → replaced with `[DATE]`
- Social Security numbers → replaced with `[SSN]`
- Addresses → replaced with `[ADDRESS]`
- Any other direct identifiers as defined under HIPAA's Safe Harbor method

**We never transmit raw PHI to any external server.**

### 2.2 Screenshots (Vision Analysis)

For certain EHR platforms, the extension may capture a screenshot of the note to extract
structured fields. Before transmission:

- A black mask is applied over the patient header area (top 120px)
- Additional masking is applied to any detected patient name regions

Screenshots are processed in memory only and are never stored.

### 2.3 Anonymized Note Text

The de-identified note text is sent to our backend service (Cloudflare Workers) for
AI-assisted analysis. This text:

- Contains no direct patient identifiers
- Is used solely to generate compliance feedback
- Is not stored on our servers after analysis
- Is not used for model training

### 2.4 User Account Data

If you create an account, we store:

- Email address
- Organization name
- Review history (anonymized note scores and feedback only — no note content)

---

## 3. AI Processing

NoteVpro ABA uses Claude (Anthropic) as its AI analysis engine. Anonymized note text
is sent to Anthropic's API for processing. Anthropic's data handling policies apply
to this transmission. We do not send raw PHI to Anthropic.

**Important:** NoteVpro ABA is currently operating under standard API terms. We are
in the process of establishing a Business Associate Agreement (BAA) with Anthropic for
full HIPAA compliance certification. Until that BAA is in place, we recommend using
the extension with de-identified or synthetic data for testing purposes.

---

## 4. Data Storage

| Data type | Where stored | Retention |
|---|---|---|
| Anonymized review scores | Cloudflare D1 (encrypted at rest) | 90 days |
| Therapist feedback | Cloudflare D1 | 90 days |
| Note text (raw or anonymized) | Never stored | N/A |
| Screenshots | Never stored | N/A |
| Auth tokens (JWT) | Browser localStorage | Session only |

---

## 5. Your EHR System

NoteVpro ABA reads content from the following EHR platforms when you are actively
using the extension on those sites:

- CentralReach (centralreach.com)
- Rethink BH (rethinkbh.com)
- Therapy Brands (therapybrands.com)
- AccuPoint (accupoint.com)
- Catalyst Health (catalysthealth.com)

The extension only activates on these domains when you explicitly trigger a review.
It does not run passively or collect data in the background.

---

## 6. Permissions Justification

| Permission | Why we need it |
|---|---|
| `activeTab` | Read the note content from the currently active EHR tab |
| `scripting` | Inject the note extractor into the EHR page |
| `storage` | Save your preferences and session token locally |
| `sidePanel` | Display review results in Chrome's native side panel |
| `alarms` | Schedule JWT token refresh before session expiry |

---

## 7. HIPAA Considerations

NoteVpro ABA is designed as a compliance-assistance tool. You are responsible for:

- Ensuring your organization's policies permit use of third-party review tools
- Verifying your BAA requirements with your payer and employer
- Not using the extension on devices that are not authorized to handle PHI

We do not offer a signed BAA at this time. We are actively pursuing this for a future
enterprise version.

---

## 8. Children's Privacy

NoteVpro ABA is designed for use by licensed healthcare professionals. It is not
directed at individuals under 18 and we do not knowingly collect data from minors.

---

## 9. Data Sharing

We do not sell, trade, or share your data with third parties except:

- **Anthropic** — anonymized note text for AI analysis (see Section 3)
- **Cloudflare** — infrastructure provider for our backend (data processed under their DPA)
- **Legal requirements** — if required by law or court order

---

## 10. Your Rights

You may at any time:

- Request deletion of your account and associated review history
- Export your review history
- Contact us to ask what data we hold about you

**Contact:** privacy@notevpro.com

---

## 11. Changes to This Policy

We will update this policy as the product evolves. Material changes will be announced
via the extension update notes in the Chrome Web Store. Continued use after an update
constitutes acceptance.

---

## 12. Contact

**VSoftware Solutions LLC**
Product: NoteVpro ABA
Email: privacy@notevpro.com
Website: https://notevpro.com
