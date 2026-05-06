# Standards & API Reference

> Project: Auto Repair Shop Management · Generated: 2026-05-04

## Industry Standards & Specifications

### ISO Standards

**ISO 18541-1:2021 — Road Vehicles: Standardised Access to Automotive Repair and Maintenance Information (RMI), Part 1: General Information and Use Case Definition**
- URL: https://www.iso.org/standard/77810.html
- Defines the use cases and scope for independent operators' access to OEM repair and maintenance information, including diagnostics, ECU reprogramming, and service procedures. Directly relevant to the project's need to surface OEM-level technical data to independent shops.

**ISO 18541-2:2021 — Road Vehicles: Standardised Access to Automotive Repair and Maintenance Information (RMI), Part 2: Technical Requirements**
- URL: https://www.iso.org/standard/77811.html
- Specifies the technical requirements for delivery of RMI (repair manuals, labour times, TSBs, wiring diagrams) to independent operators. Shapes how repair data platforms structure and expose information via web-based interfaces.

**ISO 18541-5:2018 — Road Vehicles: Standardised Access to RMI, Part 5: Heavy Duty Specific Provisions**
- URL: https://www.iso.org/standard/68659.html
- Extends RMI access requirements to heavy-duty commercial vehicles. Relevant if the platform targets fleet operators and commercial vehicle service.

**ISO 18542-1:2012 — Road Vehicles: Standardised Repair and Maintenance Information (RMI) Terminology**
- URL: https://www.iso.org/standard/53967.html
- Provides common terminology for repair and maintenance information, supporting consistent labelling and categorisation of service operations across platforms.

**ISO 3779 — Road Vehicles: Vehicle Identification Number (VIN)**
- URL: https://www.iso.org/obp/ui/en/
- Specifies the VIN structure (17-character alphanumeric code). Core to vehicle check-in, recall lookup, and service history retrieval throughout the platform.

**ISO/IEC 19845:2015 — Universal Business Language (UBL) v2.1**
- URL: https://www.iso.org/standard/66370.html
- Defines a generic XML interchange format for business documents including invoices, purchase orders, and payment notifications. Relevant to electronic parts ordering, invoice generation, and cross-system financial document exchange.

---

### W3C & IETF Standards

**RFC 7231 — Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content**
- URL: https://datatracker.ietf.org/doc/html/rfc7231
- Defines HTTP method semantics (GET, POST, PUT, DELETE, PATCH) used by all REST APIs in the ecosystem — PartsTech, NHTSA vPIC, Shopmonkey, Tekmetric, and QuickBooks Online.

**RFC 6749 — The OAuth 2.0 Authorization Framework**
- URL: https://datatracker.ietf.org/doc/html/rfc6749
- OAuth 2.0 is the authentication standard required by QuickBooks Online, Shopmonkey, Smartcar, and other integrations. The project must implement OAuth 2.0 flows for third-party integrations and its own public API.

**RFC 7519 — JSON Web Token (JWT)**
- URL: https://datatracker.ietf.org/doc/html/rfc7519
- JWT is the token format used by most REST APIs in this domain for stateless authentication and authorisation across services.

**RFC 8288 — Web Linking**
- URL: https://datatracker.ietf.org/doc/html/rfc8288
- Defines the `Link` header for RESTful pagination and resource relationships, used in paginated API responses for repair orders, vehicles, and customers.

**W3C WebSub (formerly PubSubHubbub)**
- URL: https://www.w3.org/TR/websub/
- Relevant to webhook delivery patterns used by Shopmonkey, AutoLeap, and QuickBooks Online for real-time event notifications (payment received, work order updated, customer approved estimate).

---

### Data Model & API Specifications

**ACES® 5.0 — Aftermarket Catalog Exchange Standard (Auto Care Association, 2026)**
- URL: https://www.autocare.org/data-and-information/data-standards
- Industry standard for exchanging automotive parts application data (which part fits which vehicle). ACES 5.0 (released March 2026) includes a new daily-update API for subscribing to VCdb (Vehicle Configuration database), Qdb (Qualifier database), and PCdb (Product Classification database). Essential for parts catalogue lookups and inventory management.

**PIES® 8.0 — Product Information Exchange Standard (Auto Care Association, 2026)**
- URL: https://www.autocare.org/data-and-information/data-standards
- Companion standard to ACES; governs product attribute data exchange for aftermarket parts (descriptions, pricing, images, hazmat data). PIES 8.0 released March 2026 alongside ACES 5.0 with richer attribute support.

**OpenAPI Specification 3.1 (OAS 3.1)**
- URL: https://spec.openapis.org/oas/v3.1.0.html
- The current de facto standard for describing REST APIs; achieves full alignment with JSON Schema Draft 2020-12. The project's public API should be documented in OAS 3.1 to enable automated SDK generation, interactive docs (Swagger UI / Redoc), and contract testing. OAS 3.2.0 (released September 2025) is also available.

**JSON Schema 2020-12**
- URL: https://json-schema.org/draft/2020-12
- Used for validating request/response payloads for repair orders, DVI results, inventory records, and customer data. Natively supported by OAS 3.1.

---

### Security & Authentication Standards

**PCI DSS v4.0 — Payment Card Industry Data Security Standard**
- URL: https://www.pcisecuritystandards.org/
- Required for any platform that accepts card payments for repair invoices. Using an integrated payment processor (Stripe, Square) that handles card data directly reduces the shop's PCI scope to SAQ A (self-assessment questionnaire, simplest tier). The project must document its PCI scope and use compliant payment APIs.

**OAuth 2.0 (RFC 6749) and OpenID Connect 1.0 (OIDC)**
- URL: https://openid.net/connect/
- OIDC is the identity layer built on OAuth 2.0, providing customer and technician authentication with standardised claims. Integrations with QuickBooks, Smartcar, and Shopmonkey all require OAuth 2.0 flows. OIDC can support customer-facing portals and multi-location SSO.

**OWASP Application Security Verification Standard (ASVS) 4.0**
- URL: https://owasp.org/www-project-application-security-verification-standard/
- Provides a security testing and verification framework for web applications. Particularly relevant for securing repair order data, customer PII, and payment records. ASVS Level 2 is a suitable target for this application class.

**GDPR (EU) 2016/679 — General Data Protection Regulation**
- URL: https://gdpr.info/
- Applies to shops serving EU customers and to any SaaS provider processing EU resident data. Requires lawful basis for processing, right-to-erasure support, and data breach notification within 72 hours. Vehicle service history constitutes personal data under GDPR.

**CCPA — California Consumer Privacy Act (2018, amended 2023)**
- URL: https://oag.ca.gov/privacy/ccpa
- Applies to California residents' data including vehicle service records. Requires transparent data use disclosures, opt-out of sale, and deletion rights.

---

### MCP Server Specifications

**Model Context Protocol (MCP) — Anthropic, 2024**
- URL: https://modelcontextprotocol.io/
- Open protocol for exposing tool-callable context to AI language models. A Tekmetric MCP server already exists (open source, GitHub: `beetlebugorg/tekmetric-mcp`) allowing natural-language queries over shop data (customers, vehicles, repair orders, appointments). An MCP server for the project's own platform would enable AI-native workflows: service writers querying repair history, managers asking about KPI trends, and AI agents drafting repair orders from DTC codes.

---

## Similar Products — Developer Documentation & APIs

### NHTSA vPIC & Recalls API

- **Description:** Official US government APIs for VIN decoding, manufacturer data, and safety recall lookups by VIN, make, model, and model year. Free, no authentication required.
- **API Documentation:** https://vpic.nhtsa.dot.gov/api/ and https://www.nhtsa.gov/nhtsa-datasets-and-apis
- **Key Endpoints:** `GET /vehicles/DecodeVin/{vin}` for VIN decode; `GET api.nhtsa.gov/recalls/recallsByVehicle?make={MAKE}&model={MODEL}&modelYear={YEAR}` for recall data; batch decode up to 50 VINs at once.
- **Data Formats:** JSON, XML, CSV (selected via `?format=` parameter)
- **Authentication:** None required; rate limiting enforced automatically
- **Standards:** REST/JSON; supports partial VIN (less than 17 characters)
- **SDKs/Libraries:** Multiple community wrappers available; Apify-hosted OpenAPI definition available

### PartsTech External API

- **Description:** Parts ordering and catalogue API connecting shops to 20,000+ parts stores and 6 million parts. Powers parts search, fitment verification, and electronic ordering inside shop management systems.
- **API Documentation:** https://api-docs.partstech.com/
- **Integration Guide:** https://www.partstech.com/m/api
- **Standards:** REST/JSON; two integration modes: Punchout API (fastest to develop) and Full API (full catalogue access)
- **Authentication:** API key-based (partner programme required)
- **SDKs/Libraries:** Not publicly listed; partner support provided

### Mitchell RepairCenter API

- **Description:** OData/REST API exposing OEM repair data, labour times, technical service bulletins, and parts information. Used by independent shops needing access to manufacturer-level service data.
- **API Documentation:** https://developer.mitchell.com/apis
- **Developer Portal:** https://developer.mitchell.com/
- **Standards:** OData protocol over REST; Microsoft OData query syntax
- **Authentication:** Partner agreement required; details at developer.mitchell.com
- **Contact:** developer.support@mitchell.com

### Shopmonkey API

- **Description:** Cloud-native shop management platform offering a REST API v3 for customers, repair orders, vehicles, inventory, appointments, and payments. Supports webhooks for real-time event delivery.
- **API Documentation:** https://shopmonkey.dev/
- **Developer Portal:** https://developer.shopmonkey.io/
- **Standards:** REST/JSON, OpenAPI; webhooks for event-driven integration
- **Authentication:** OAuth2 Bearer tokens; API keys generated via dashboard or API
- **Base URL:** `https://api.shopmonkey.cloud/v3`
- **Rate Limiting:** `x-ratelimit-*` headers; 11 data centres across North America
- **SDKs/Libraries:** Not separately listed; REST-native

### Tekmetric API

- **Description:** Shop management API exposing shop data (customers, vehicles, repair orders, KPIs, appointments) and supporting external integrations. An open-source MCP server (`beetlebugorg/tekmetric-mcp`) enables AI natural-language queries over shop data.
- **API Documentation:** https://api.tekmetric.com/changelog
- **API Tracker Entry:** https://apitracker.io/a/tekmetric
- **Standards:** REST/JSON; GraphQL also supported
- **Authentication:** API access requested from Tekmetric; bearer tokens
- **Notable:** Stripe integration for payments (see https://stripe.com/customers/tekmetric)

### QuickBooks Online Accounting API

- **Description:** Intuit's REST API for full accounting integration: invoices, payments, customers, vendors, bills, and financial reports. Used by AutoLeap, Shopmonkey, MaxxTraxx, and others for real-time bookkeeping sync.
- **API Documentation:** https://developer.intuit.com/app/developer/qbo/docs/develop
- **API Reference:** https://developer.intuit.com/app/developer/qbo/docs/api/accounting/all-entities/account
- **Standards:** REST/JSON; OAuth 2.0 + OpenID Connect; webhooks for real-time change notifications
- **Authentication:** OAuth 2.0 (Authorization Code flow); tokens managed via Intuit Developer Portal
- **SDKs/Libraries:** Official SDKs for Java, PHP, Python, Node.js, .NET, Ruby

### Stripe Payments API

- **Description:** Industry-standard payment processing API supporting online payments, in-person terminals, Buy Now Pay Later, and B2B payment terms. Used by Shopmonkey and Tekmetric for payment collection.
- **API Documentation:** https://docs.stripe.com/api
- **Developer Documentation:** https://docs.stripe.com/
- **Standards:** REST/JSON; PCI DSS Level 1 certified; SAQ A scope for standard integrations
- **Authentication:** API key (publishable + secret key pair); webhook signing for event verification
- **SDKs/Libraries:** Official SDKs for JavaScript/Node.js, Python, Ruby, PHP, Java, Go, .NET
- **PCI Guide:** https://stripe.com/guides/pci-compliance

### Smartcar Connected Vehicle API

- **Description:** Vehicle telematics API providing standardised access to OBD-II, battery level, odometer, fuel level, tyre pressure, location, and remote commands (lock/unlock, charge control) across connected vehicles from major manufacturers.
- **API Documentation:** https://smartcar.com/docs/api-reference/intro
- **API Reference:** https://smartcar.com/docs/api/
- **Standards:** REST/JSON; OAuth 2.0 for consumer consent; ISO 27001 and GDPR compliant
- **Authentication:** Client ID / Client Secret exchanged for access tokens (valid 1 hour); OAuth 2.0 authorization flow for driver consent
- **SDKs/Libraries:** Node.js (npm: `smartcar`), Python (PyPI: `smartcar`); Postman collection available
- **Base URL:** `https://vehicle.api.smartcar.com/v3`
- **Use Case for Project:** Proactive maintenance triggers from live vehicle data (odometer milestones, tyre pressure, fuel level) surfaced to customers via the shop management platform

### CARFAX for Business API

- **Description:** Vehicle history report API providing accident records, service history, ownership records, recall status, and title information via VIN lookup. Used by Shopmonkey and Tekmetric for customer-facing transparency and service history checks.
- **API Documentation:** Available via Carfax Business Development (not public)
- **Integration Contact:** https://www.carfax.com/business/
- **Standards:** REST/JSON (partner agreement required)
- **Authentication:** API keys; requires a Service Data Transfer Facilitation Agreement
- **Note:** Not publicly subscribable; requires direct commercial agreement with CARFAX

### Auto Care Association Data APIs (ACES/PIES)

- **Description:** Official subscription APIs for the ACES (vehicle fitment) and PIES (product attributes) databases, enabling daily updates to VCdb, Qdb, PCdb, PAdb, and Brand Table. Released November 2024; supports ACES 5.0 and PIES 8.0 (March 2026).
- **API Documentation:** https://www.autocare.org/data-and-information/data-standards
- **Standards:** REST; previously periodic manual downloads, now daily delta updates
- **Authentication:** Subscription required through Auto Care Association membership or licensing
- **SDKs/Libraries:** Not separately listed; partner documentation provided

---

## Notes

- **OBD-II and Telematics Integration:** The SAE J1979 (OBD-II) standard governs diagnostic port protocols and DTC (Diagnostic Trouble Code) definitions. While not an internet API standard, a future AI diagnostic feature would ingest J1979-compliant DTC codes from scan tools or telematics devices (Smartcar, High Mobility).

- **Emerging: Vehicle-to-Cloud (V2C) Standards:** The COVESA (Connected Vehicle Systems Alliance) and AutoSAR Adaptive standards are emerging for direct vehicle-cloud data pipelines. These are not yet mainstream for independent repair shops but will become relevant as connected vehicle density increases.

- **OASIS Automotive Repair TC:** OASIS completed an Automotive Repair Information TC that defined an XML format for emissions-related repair and diagnostic information (scope: EU Directive 70/220/EEC). This work is dated (completed 2003) but historically relevant to the RMI access requirements now codified in ISO 18541.

- **MCP Opportunity:** The existence of an open-source Tekmetric MCP server (`beetlebugorg/tekmetric-mcp`) signals that AI-native interfaces to shop data are already emerging. The project should consider publishing an official MCP server alongside its REST API to enable third-party AI integrations with minimal friction.
