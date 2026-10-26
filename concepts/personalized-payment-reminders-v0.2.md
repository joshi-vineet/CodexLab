# Personalized Payment Reminders — Product Concept v0.2

**Status:** Proposed for manager review (not approved)  
**Version:** 0.2  
**Scope:** Release 1 — payment reminder timing and delivery-channel preferences

## Opportunity
Credit cardholders have different payment routines and communication preferences. A fixed reminder schedule or single channel may be less useful than a cardholder-selected option. Give eligible cardholders control over when they receive an upcoming payment reminder and through which eligible channels, without changing their contractual due date or mandatory communications.

## Target users and problem
Eligible credit cardholders who want to manage optional upcoming-payment reminders. They need an understandable self-service way to select preferences and revisit them later.

## Proposed MVP
1. Offer one reminder lead time: **1, 3, or 7 days before the payment due date**.
2. Let customers choose **one or more** supported delivery channels from **email, SMS, and mobile push**, subject to valid contact details, device eligibility, and applicable consent.
3. Allow customers to **view and update** saved preferences.
4. Show clear **success or failure confirmation** after saving.
5. **Persist** preferences for subsequent billing cycles, subject to account eligibility and policy.

Proposed entry points: mobile app and authenticated web account management, subject to technical feasibility. Apply shared preference behavior where possible.

### Conceptual journey
Account settings → Payment reminder preferences → Select one lead time → Select eligible channels → Review and save → Receive confirmation → Return to view or change settings.

### Illustrative acceptance criteria (to refine in PRD)
- Given an eligible cardholder opens settings, when reminder preferences load, then the saved lead time and enabled channels are displayed.
- Given an eligible cardholder selects one lead time and at least one eligible channel, when they save and the operation succeeds, then the service persists the selections and displays confirmation.
- Given no eligible channel is selected, when the cardholder tries to save, then the interface explains the validation requirement without claiming changes were saved.
- Given a save request fails, when the error is returned, then the interface displays a failure message and does not falsely confirm persistence.
- Given a cardholder returns in a later session, when their preferences load, then the latest successfully saved choices appear.

## Out of scope for Release 1
- Arbitrary clock-time scheduling and multiple reminder lead times in the same billing cycle.
- AI-based recommendations, personalized send-time optimization, and advanced follow-up sequences.
- New payment-aware suppression or payment-status orchestration logic (existing mandatory safeguards and compliance rules must still be honored).
- Changes to due dates, billing terms, autopay enrollment, or required servicing notices.

## Dependencies and review questions
- Confirm existing notification scheduler capabilities, event sources, and delivery-channel availability.
- Verify consent, communication preferences, SMS rules, device token eligibility, verified contacts, accessibility, and required notices.
- Determine policy for customers on autopay, already-paid accounts, delinquent accounts, account closure, holidays/time zones, and preference changes near a send cutoff.
- Confirm supported entry points (mobile app and website) and whether one shared preference service can be used.
- Define observability for successful saves, delivery attempts, and customer-facing errors.

## Hypotheses and measurement
The feature may improve perceived relevance of reminders and help on-time payments; no quantified outcome is established.
Pilot measurements: eligible-account activation/opt-in, preference setup completion, successful persistence, reminder delivery and failure rates per channel, notification complaints, and on-time payments against an appropriate comparison group. Set baselines and targets only after access to real performance and compliance data.

## Options considered
- **A: Basic preferences (selected MVP)** — preset lead time plus chosen channel(s); lowest scope and fastest validation, subject to feasibility.
- **B: Payment-aware adaptive reminders (later)** — add new payment-state-triggered suppression and follow-ups; greater integration/policy work.
- **C: Intelligent timing (later)** — predictive recommendations; higher data, consent, and explainability complexity.

## Evidence and boundaries
This concept is a **proposed product hypothesis**, not a statement of existing Synchrony capabilities, priorities, or commitments. Prior internal discovery surfaced **fictional demonstration materials** relating to standard due-date email reminders and SMS reminder choice; those references do **not** verify deployed systems, actual financial KPIs, or funded initiatives. No confidential SharePoint text, customer data, or internal-only operational claims are reproduced here. Public competitor practices should be validated against dated first-party product documentation before being used to support implementation or investment decisions.

## Decisions requested from reviewer
1. Endorse timing + channel preferences as the Release 1 scope.
2. Confirm target segment, account eligibility, and initial delivery channels.
3. Approve feasibility discovery for notification infrastructure and consent/compliance.
4. Confirm mobile/web entry-point assumptions.
5. Agree on pilot design and measurable success criteria before investment decision.

## Version history
- **v0.1:** Broad personalized reminder concept, including possible follow-ups and payment-aware logic.
- **v0.2:** Narrowed first release to preset reminder timing, channel choice, and preference management; deferred intelligence, new suppression, and advanced scheduling.
