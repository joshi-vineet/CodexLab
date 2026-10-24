# CPR-001 v0.3 — My Payment Reminders
Status: Proposed concept for product manager review (not approved)
Date: 2026-10-25
Product context: Consumer credit card servicing
Public-safe concept: no confidential source material or internal architecture

## Opportunity and problem
Cardholders have different payment routines. A reminder delivered at an unsuitable time or through an inconvenient channel may be less useful. Existing notification options across the industry suggest that customer control over reminder delivery is a useful baseline experience. The extent of current functionality in the intended product must be validated before estimating net-new scope.

## Intended users and outcome
Primary users: eligible consumer credit cardholders, especially those who pay manually and use verified digital contact methods.
Desired outcome: cardholders can choose **when** a payment reminder is sent relative to its due date and **how** it is delivered, without changing contractual payment obligations or required communications.

## Recommended Release 1
- Offer one configurable optional payment reminder per billing cycle: 1, 3, 5, or 7 **calendar days** before the payment due date.
- Allow selection of email, SMS, or both, subject to channel availability, verified contact details, and applicable permission/consent controls.
- Display current preferences, support edits, preview the selected schedule, and acknowledge successful saves.
- Use existing approved send-time windows and existing production payment/notification eligibility rules.
- Preserve existing settings until the cardholder changes them. Apply updates to future eligible sends subject to scheduling cutoffs.
- Record changes and reminder scheduling/dispatch/delivery status for quality measurement and audits.

## User journeys
1. **Set up:** Sign in → open payment reminder settings → choose lead time and channel(s) → review → save → confirmation.
2. **Edit:** Return to settings → view saved choices → edit → save; future eligible reminders follow the updated values.
3. **Receive:** For an eligible reminder event, retrieve valid saved settings → schedule/dispatch through authorized selected channel(s) → record delivery status where available.

## Requirements (concept-level)
- REQ-001: Show available reminder lead times (1/3/5/7 calendar days).
- REQ-002: Support authorized email, SMS, or both choices.
- REQ-003: Validate contact and consent eligibility before saving and sending.
- REQ-004: Persist and retrieve account-level settings.
- REQ-005: Respect the selected lead time and existing send windows when scheduling.
- REQ-006: Allow subsequent preference updates with clear effective-date/cutoff handling.
- REQ-007: Record preference changes and reminder lifecycle events, avoiding sensitive content in analytics.
- REQ-008: Preserve mandatory service and regulatory communications independently from optional reminders.

## Explicit exclusions
No new payment-aware suppression, AI recommendations, custom clock-time scheduling, push channel, paycheck-linked scheduling, consolidated account digests, payment initiation, due-date changes, changes to credit terms, or replacement of mandatory statements/notices.

## Differentiation and options considered
- Option A: Channel-only settings — simplest, but little additional control.
- **Chosen Option B: Lead-time + channel preferences** — small customer-facing scope and testable customer value; must first assess overlap with existing alert capabilities.
- Option C: Payment-aware/adaptive reminders — potentially more relevant but requires additional payment-state integration and greater operational controls; deferred.

## Success measures and proposed experiment
**Primary launch KPI — preference adoption:** unique eligible treatment customers who save valid preferences / unique eligible treatment customers exposed to the feature. Illustrative planning target: 30%; confirm against baseline.
**Setup completion:** unique customers saving / unique customers starting setup.
**Preference compliance (operational quality gate):** eligible reminder events correctly scheduled and routed according to valid effective preferences / all eligible reminder events with valid preferences. Illustrative planning target: 99.5%; baseline and tolerance pending validation.
**Delivery quality:** provider-confirmed delivery / attempted deliveries where such confirmation exists; separately report submission, delivery, and unknown.
**Customer guardrails:** complaints and opt-outs per 1,000 enrolled cardholders, unauthorized sends, duplicates.
**Secondary business outcome:** on-time minimum-payment rate = eligible accounts meeting minimum due by due date / eligible accounts due, comparing randomized treatment and control on an intention-to-treat basis.
Pilot design proposal: customer-level randomized 50/50 control (existing alerts) vs treatment (new preference settings), with eligibility and power determined before launch; an illustrative 8–12-week duration may cover several payment cycles. Do not assume uplift or statistical significance. Pre-register baselines, measurement windows, sample size, and segment analyses.

Events to instrument: preferences_viewed, preferences_started, preferences_saved, preferences_updated, reminder_scheduled, reminder_dispatched, reminder_delivery_status, payment_due_outcome. Use tokenized identifiers and approved retention.

## Tradeoffs, risks, and dependencies
- One reminder is easier to build and less noisy than flexible multi-reminder sequences.
- SMS + email provides practical reach but adds consent and delivery dependencies.
- Calendar-day lead times simplify choice but require clear timezone/send-cutoff rules.
- Preserve existing operational payment rules: this release must not promise that reminders stop immediately after a payment.
- Review channel eligibility, consent, required servicing notices, accessible interfaces, processing delays, delivery failure behavior, and account-level eligibility.
- Confirm existing product capability and any overlapping roadmap work before committing implementation.

## Evidence and limitations
Public information indicates that several U.S. card issuers provide payment/account alert options. Illustrative public reference points (not proof of precise feature parity):
- Synchrony account alerts: https://www.synchrony.com/help/account-management
- Chase account alerts: https://www.chase.com/personal/mobile-online-banking/login-alerts
- Capital One payment support: https://www.capitalone.com/help-center/credit-cards/late-payment-support/
Specific current feature coverage must be reconfirmed during discovery. No internal SharePoint content is reproduced here.

## Open validation questions
1. What reminder timing and channels are already supported for the targeted cardholder population?
2. Which changes are UI-only vs notification scheduling or service changes?
3. What contact verification, channel authorization, and regulatory constraints apply?
4. What are eligibility, effective-date cutoff, timezone, and fallback rules?
5. Which analytics events and payment outcome data are available for experimentation?

## Version history
- v0.1: broad personalized payment-reminder concept.
- v0.2: explored timing, channels, payment awareness, and actionable reminders.
- **v0.3: narrowed first release to timing and channel preferences only;** adopted adoption/compliance KPIs and controlled outcome evaluation.

## Review requested
Product manager: assess customer need, duplication with existing capabilities, Release 1 boundaries, consent and delivery risks, and experiment quality. Record decision against this exact proposed version. No approval is claimed.
