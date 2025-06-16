Here's the complete content of the `README.md` file, including the standard Markdown syntax for headings. You can **copy and paste this directly** into your GitHub `README.md` file.


# System Design Challenge: Tenant Profiling Software

This repository contains a detailed system design for a **Tenant Profiling Software**. This document outlines the architectural choices, component breakdowns, data models, API designs, and strategies for scalability, security, monitoring, and disaster recovery, all in response to a challenging system design interview prompt.

---

## Problem Statement

You are tasked with designing the core backend and infrastructure for a **Tenant Profiling Software** aimed at landlords, property managers, and real estate agents. The primary goal of this system is to streamline tenant vetting by providing comprehensive risk assessments. The system needs to support multiple interaction channels, including a web portal and WhatsApp, and handle sensitive personal and financial data securely.

---

## Core Requirements

1. **Tenant Inquiry**: Allow users (landlords, property managers, agents) to submit requests for tenant profiles using an individual's national ID number or a company's registration number.

2. **Credit Bureau Integration**: Integrate with a third-party **Tenant Profile Network (TPN) API** to fetch detailed tenant data, including lease history, financial defaults, and legal notices.

3. **Report Generation**: Generate detailed, comprehensive risk assessment reports based on the retrieved TPN data. These reports should be available in a downloadable PDF format.

4. **Web Portal**: Provide a responsive web application where users can initiate inquiries, view generated reports, and manage their account.

5. **WhatsApp Integration**: Enable users to initiate tenant inquiries by sending structured messages to a dedicated WhatsApp Business number. The system should also be able to send summarized reports and notifications back to users via WhatsApp.

6. **User Management**: Implement secure user authentication (registration, login, password management) and role-based access control (e.g., Admin, Property Manager, Landlord, Support Agent) to manage what each user type can do and see.

7. **User Support**: Offer multi-channel support for users, including an in-app chat feature on the web portal and direct chat support via the WhatsApp Business account.

---

## Non-Functional Requirements

1. **High Availability & Reliability**: The system must be highly available (e.g., 99.9% uptime) and resilient to failures, with no single points of failure.

2. **Scalability**: The system should be designed to scale to accommodate a rapidly growing user base (e.g., hundreds of thousands of users) and a high volume of daily inquiries (e.g., millions of inquiries per month, with potential peak loads).

3. **Performance**:

   * TPN inquiry processing (fetching data from TPN API) should be efficient, ideally completing within 5-10 seconds, depending on the external API's response time.

   * Report generation should be asynchronous and notify the user upon completion.

   * Web application load times should be fast.

4. **Security**:

   * All sensitive data (personal IDs, financial records, API keys) must be encrypted both in transit (e.g., HTTPS/TLS) and at rest (e.g., database encryption).

   * Robust authentication and authorization mechanisms (e.g., strong passwords, JWTs, RBAC).

   * Protection against common web vulnerabilities (OWASP Top 10).

   * Rate limiting for all external API calls and user-facing endpoints.

5. **Compliance**: Strict adherence to data privacy regulations, specifically South Africa's **POPIA (Protection of Personal Information Act)** and **GDPR** principles for data handling, consent, and user rights.

6. **Auditing**: Comprehensive logging of all user actions, data access, and system events for compliance, security, and debugging purposes.

---

## Assumptions & Clarifications

* The TPN API is a standard RESTful API with documentation and authentication (assume API keys).

* The WhatsApp Business API is managed by Meta and provides webhooks for incoming messages and REST endpoints for outgoing messages.

* You do not need to design the UI/UX visually, but consider the implications of different channels on user interaction.

* Assume the system will be deployed on a cloud platform (e.g., AWS, Azure, GCP – you can choose one and specify services).

---

## Deliverables for the Candidate

Please provide a detailed system design covering the following aspects:

1. **High-Level Architecture Diagram**: Illustrate the major components, their interactions, and data flow.

2. **Component Breakdown**:

   * For each major service/component (e.g., Authentication Service, TPN Integration Service, Report Generation Service, WhatsApp Handler, Support Service, User Management), describe its responsibilities, chosen technology stack (e.g., Python/Django for backend, React for frontend), and key considerations (e.g., design patterns, specific libraries).

3. **Data Model Design**:

   * Outline the core entities (e.g., `User`, `TenantEnquiry`, `TPNReport`, `SupportTicket`, `ChatMessage`) and their relationships.

   * Indicate key fields and data types, especially for sensitive information.

4. **API Design**:

   * Define key REST API endpoints for the web portal and internal services (e.g., `/api/tenants/enquiry`, `/api/reports/{id}`, `/api/support/chat`).

   * Briefly describe input/output for each.

5. **Scalability Strategy**:

   * Detail how each layer (frontend, backend, database, external integrations) will scale to meet high demand.

   * Discuss techniques like horizontal scaling, load balancing, caching, and asynchronous processing.

6. **Security Deep Dive**:

   * Explain the authentication and authorization flows (web and WhatsApp).

   * Describe encryption strategies for data in transit and at rest.

   * How would you handle API keys and secrets?

   * Strategies for input validation and protection against common attacks.

7. **Monitoring & Logging Strategy**:

   * How will you monitor the health, performance, and security of the system?

   * Where will logs be stored and how will they be analyzed?

8. **Disaster Recovery & Reliability**:

   * Briefly describe your strategy for ensuring data durability and minimizing downtime in case of component failures or regional outages.

---

## Bonus / Discussion Points (Optional)

* How would you manage TPN API rate limits and potential throttling/failures from the external service?

* What are the key challenges in verifying user identity when interacting solely via WhatsApp, and how would you address them?

* Discuss the trade-offs between a monolithic Django application and a microservices approach for this system.

* How would you ensure real-time updates for support chat both in-app and on WhatsApp?

* Consider the implications of GDPR's "right to be forgotten" or POPIA's equivalent on your data model and data retention policies.
  
