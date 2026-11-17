# Email MKT – Handoff (Data Security campaign, 11/2026)

Read this first in a new session, then load the `email-marketing-bible` skill.

## Goal
Build an end-to-end email workflow with the Marketing Manager: brief → plan → draft in Brevo → review → approve → schedule. This campaign is the pilot.

## Sources
- Campaign plan (content direction, Campaign tracker tab, Rules tab): https://docs.google.com/spreadsheets/d/1znZMJWKIEB1TVsW2oFDsBkVrcMtdlDJuspwUESaDARA/edit?gid=110
- Email Marketing Plan | 2026 (BS Schedule tab, Checklist tab): https://docs.google.com/spreadsheets/d/1l64Pi_zPVlJ39EA0tPDwpT2SQ-86oPnYOwrJP11N890/edit
- UTM convention (tab "(3) UTM Request"): https://docs.google.com/spreadsheets/d/1RlAR28HOAvCsEG6xdSRIfyJmIrPr6Bca1Dydo8ik8dM/edit?gid=999161296

## Progress
- [x] Step 1 – 4 emails added to BS Schedule rows 35–38 (Status: Planning)
- [ ] Step 2 – Review past `BS_` campaigns/templates in Brevo (blocked: Brevo API key not loaded in first session)
- [ ] Step 3 – Draft each email in Brevo (VN first, then APAC)
- [ ] Step 4 – Manager reviews content + design
- [ ] Step 5 – Final approval
- [ ] Step 6 – Schedule (only after the manager types "send it" on the send packet)

## Schedule
| Date | Segment | Email | Subject (from plan) |
|---|---|---|---|
| 19/11 | VN | VN E1 (VI) | Khách vừa đặt hàng đã bị gọi lừa: anh/chị kiểm tra nhanh 3 chỗ này |
| 20/11 | APAC | APAC E1 (EN) | Vietnam storefront: a data-leak wave and a new law |
| 26/11 | VN | VN E2 (VI) | Đã làm hết mà khách vẫn bị gọi lừa? Có thể vấn đề không nằm ở shop |
| 26/11 | APAC | APAC E2 (EN) | 7 checks for your Vietnam storefront |

Full copy is in the Campaign tracker tab (column "Suggesting content").

## Decisions made
- Segments: split by region in the BS database. BS Schedule shows only "VN" / "APAC". Find the matching Brevo segment, then confirm name + contact count with the manager before scheduling. Always exclude "OT Only (No BS)" (shared Brevo account).
- UTM (convention 8/2026, Email MKT row): `?utm_source=email_mkt&utm_medium=email_mkt&utm_campaign=data_security_2026&utm_content={vn_e1|vn_e2|apac_e1|apac_e2}` (campaign/content names proposed, awaiting confirmation).
- Sender: BSS Commerce <consultant@bsscommerce.com>.
- Campaign name in Brevo: `BS_[Name]_DDMMYY`.

## Brevo checklist (from Checklist tab)
- Greeting: `Hi {{ contact.FIRSTNAME | default: "there" }}` (EN). VN: use "anh/chị" default.
- Font Roboto, size 14, line spacing 1.5. Padding desktop 10/10/0/0, mobile 10/10/15/15.
- Colors: brand colors; light blue #dceaff, gray #f0f0f0.
- Saved sections: BS_Signature_Desktop / BS_Signature_Mobile, BS_Social_Desktop / BS_Social_Mobile.
- Advanced settings: only Subscription → custom unsubscribe page, type Default.
- Check credits when creating the campaign (credits renew on the 11th each month).

## Content rules (Rules tab)
- Never name Sapo or any specific local platform.
- Do not frame "local = risky, global = safe".
- Do not promise that switching platform ends data leaks.
- Law-related claims (PDPL, from 01/01/2026) need legal review: VN E2, APAC E1, APAC E2.

## Open items
1. Booking link `[LINK ĐẶT LỊCH]` missing (blocks all 4 emails). Also check whether it is a Brevo form on bsscommerce.com (UTM captured) or an external tool (UTM lost).
2. Blog /vi must be live (planned 18/11) before VN E1 sends 19/11. Blog /en planned 23/11 for APAC E2.
3. Confirm utm_campaign / utm_content names.
4. Checklist tab still shows the old UTM (`BS_email_mkt`), which contradicts the 8/2026 convention. Proposed to update it; waiting for OK.
5. VN subjects are ~65–68 chars; propose shorter versions (~45) at draft time.
6. APAC segment is all of APAC, broader than the target "brands present in Vietnam". Discuss narrowing or reframing the subject.
7. Brevo API: key must be in env var `BREVO_API_KEY` (header `api-key`); `api.brevo.com` is allowed. Watch for "Authorised IPs" blocking.
