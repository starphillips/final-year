
#### 1. Build a stakeholder register. For each stakeholder, record their role, goals, concerns, influence and interest, and what they’re allowed and not allowed to do.

**Output:** A stakeholder table, a power/interest grid, and an i* Strategic Dependency (SD) model showing actors and the goals they have.

#### 2. Identify dependencies and conflicts between clinical, admin and finance


**Conflicts to cover:**
- Clinicians want less admin recording, while managers want full accountability data.
- Urgent treatment can’t wait for payment confirmation.
- Finance needs clinical context for refunds but must not judge whether treatment is clinically necessary.
- Call handlers need enough information to help callers, but access should be the minimum their role needs.
- The follow-up window the clinician asks for may not match available slots.
- Patients prefer different ways of being contacted, but the letter and phone deadlines are fixed.
- Teams currently work in inconsistent ways.

**Output:** i* SD/SR models and a conflict table (conflict, stakeholders involved, proposed resolution or trade-off).

#### 3. Information and authorisations at each stage
- referral 
- consultant review 
- new patient appointment (NPA) booking 
- contact patient
- Patient attends NPA - discusses treatment with consultant and clinical team
- Consent and Treatment Booking Request 
- Chemotherapy Bookings Team receives the authorised request 
- Patient receives information about the Clinical Nurse Specialist Team
- funding/payment - finance team to record the details and processes for payment delays, cancellations, refunds and urgent treatment regardless of payment
- treatment cycles confirmed
- Cycle reviews
- modifications 
- letters 
- follow-up 
- cancellations, did-not-attend (DNA) and discharge 
- enquiries.

**Output:** One table with these columns:
    - Stage
    - Data needed in and produced
    - Who can act
    - Who must authorise
    - What’s explicitly forbidden (e.g. secretaries can’t judge clinical suitability)
    - What gets audited

Then turn the table into a role-based access control (RBAC) matrix of roles × actions/data. This table is the backbone of most of your functional and security requirements.

#### 4. Analyse external service interactions
**Do:** For each external service (scheduling, correspondence, clinical services like labs/imaging/treatment, PSP), define what is sent, what comes back, and the expected timing.

**Output:** A context diagram and sequence diagrams for the tricky flows:
	- Booking via external scheduling
	- Payment request and its callback
	- Refund
	- Letter dispatch

#### 5. Identify possible failures and delays

**Do:** Build a failure/exception analysis. Most of the scenarios are already in the case:
    - Missing referral documents
    - Phone unanswered or wrong number
    - No suitable appointment available in time
    - External service down (booking stays pending, no duplicates)
    - Payment declined, cancelled, duplicated or incomplete
    - Payment taken but confirmation lost (mark for investigation, never re-charge)
    - Urgent treatment without payment
    - Informal treatment-change requests (email or phone)
    - Letters overdue past 7 days, 1 month or 3 months (escalation)
    - DNAs and cancellations after payment
    - Wrong-patient matching
    - System downtime

**Output:** A failure table (trigger, impact, detection, required system behaviour, linked requirement) or a light FMEA. BPMN models should show these as error and timer events, e.g. the 7-day, 1-month and 3-month letter timers.

#### 6. Propose functional requirements for an effective Hospital Patient Administration System. 

**Do:** Group them by area: Referral, Booking, Patient Contact, Treatment, Funding and Payment, Refunds, Correspondence, Enquiries, Pathway Monitoring, Reporting, Audit.

**Format:** Give each one an ID, a “The system shall…” statement, a source (case paragraph or stakeholder), a priority (MoSCoW) and acceptance criteria. The acceptance criteria tie into the testing learning outcome (MO4).

#### Propose non-functional requirements for an effective Hospital Patient Administration System. 

Make them measurable where you can:

- Security and privacy: UK GDPR/DPA 2018, RBAC, authentication, encryption in transit, no card data stored (PCI DSS).
- Audit: Records are immutable and show who, when and what.
- Availability: Including a downtime recording procedure.
- Data integrity: Patient matching using NHS number plus other identifiers.
- Performance.
- Usability: Minimal clinician data entry.
- Accessibility: Accessible formats, translation, authorised representatives.
- Interoperability: Integration with the external services.
- Idempotency: No duplicate bookings or charges.

#### 7. Identify the ambiguity

Where the case does not provide sufficient information - consult the appropriate stakeholders (Tutors) where possible and document reasonable assumptions.

Do: Keep a running log with these columns: issue, why it matters, question for tutor, tutor answer, and the assumption you made if you got no answer.


