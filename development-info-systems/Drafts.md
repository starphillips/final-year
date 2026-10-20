## Project Scope

The implemented system covers the patient pathway from receiving a referral to booking treatment. The core scope is sized for a team of four, with extensions are planned, depending on team capacity. Areas outside the implemented scope are still covered in our analysis and models. 

### Core Scope 

1. Referral intake 

The referral is matched to an existing patient record, with a duplicate check to avoid creating a second record. Medical Secretaries check the supporting documents and request anything missing from the referring organisation. 

2. Consultant review 

The Consultant accepts, rejects, requests more information or redirects the referral, with the reason and the decision-maker recorded. Urgent referrals follow a fast-track route. 

3. Outpatient booking 

A booking request goes to the Outpatient Bookings Team, and appointments are found through a mock external scheduling service. Every patient gets a letter, and a phone call as well if the appointment is within two weeks. Every contact attempt and its outcome is recorded. If no slot is available within the requested timeframe, the case is flagged rather than booked outside it. 

4. Treatment booking 

The Consultant records consent and creates an authorised Treatment Booking Request. The Treatment Bookings Team then checks availability with external providers. If a provider is unavailable, the booking stays pending and is retried without creating duplicate appointments. 

### Extensions (capacity dependent) 

5. Finance 

A funding check, payment through a mock Payment Service Provider, handling of declined payments and retries, payments where confirmation never arrives (marked for investigation), and an urgent clinical override that lets treatment go ahead before payment is confirmed. 

6. Cancellations, failures to attend and refunds 

Cancellations and failures to attend are recorded, paid appointments are referred to Finance, and Finance approves refunds through the payment provider. (Refunds depend on Extension 5.) 

  

### Across the whole system: 

- Users log in with role-based access  
- A basic audit trail records who made each key decision and when. 
- Urgent override processes for referrals and bookings 

  

### Conflicts we will address: 

- The balance between less admin recording and accountability documentation, captured by the automatic basic audit trails 
- Urgent treatment appointments and referrals  
- Authentication users based on role and limiting capabilities to that role 

  

### Out of scope (analysed in the models but not implemented): 

- Management reporting and dashboards 
- Treatment Modification Requests and changes to treatment schedules 
- Chemotherapy cycle reviews and blood tests  
- Clinic letters 
- Follow-up appointments 
- Clinical Nurse Specialist team information and contact 
- Call handling and enquiry routing 
- Change requests to treatment schedules 
- Patient expectation and communication preferences (accessible formats, translation, authorised representatives) 
- Integration with real hospital, scheduling or payment systems 

  

### Assumptions: 

- All external services are simulated. No real hospital systems or patient data are used. 
- Without Extension 5, all treatment is assumed to be funded, so no payment check runs before treatment is confirmed. 
- The system starts with test patient records and test staff accounts for each role. 
- Rules for what counts as urgent are to be confirmed with the client. 
- Rules for what should happen when there are no slots to available within the requested timeframe to be confirmed with the client. (Currently under 3, the case is flagged on the system) 