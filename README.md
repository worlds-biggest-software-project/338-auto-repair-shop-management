# Auto Repair Shop Management

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native, open-source shop management platform for independent auto repair businesses — repair orders, parts inventory, technician time, and customer notifications in one place.

Auto Repair Shop Management is a candidate project to build a cloud-native operating system for independent and multi-location auto repair shops. It targets service writers, technicians, and shop owners who today depend on closed, subscription-only platforms that lag on AI-assisted diagnostics, computer-vision inspections, and predictive parts planning.

---

## Why Auto Repair Shop Management?

- Incumbents (Mitchell 1, Tekmetric, AutoLeap, Shopmonkey, Shop-Ware, Protractor, Orderry, Garage360, Bay-Master, MaxxTraxx) are all proprietary SaaS with subscription pricing — no open-source alternative was identified during research.
- Most platforms still treat digital vehicle inspections as manual photo capture; few apply computer vision to flag wear or cross-reference OEM specifications automatically.
- Parts inventory across the category is largely reactive — driven by reorder points rather than demand forecasting based on local vehicle demographics and make/age mix.
- VIN-level NHTSA recall checks and TSB monitoring are rarely automated at check-in, despite clear liability and upsell value.
- Entry-level pricing around USD 104/month is accessible, but shops still run multiple disconnected tools (accounting, communication, inspections); an open, integrated stack reduces fragmentation and vendor lock-in.

---

## Key Features

### Repair Order & Workflow Management

- Estimates, work orders, and invoices with service history tracking
- Technician and labour time tracking with task assignment
- Mobile technician app for task management
- Workflow customisation to match shop-specific processes

### Parts & Inventory

- Parts inventory tracking with reorder points and supplier integration
- Multi-vendor parts catalogue access and electronic ordering
- Margin and pricing controls
- Demand forecasting based on vehicle age and make mix in the local market

### Digital Vehicle Inspections

- Photo and video capture with customer approval workflow
- Computer vision analysis of inspection photos to flag wear levels
- Cross-reference with OEM specifications to generate condition reports
- Customer-facing reports with recommended services

### Customer Communication & Payments

- Estimates and invoices delivered via SMS and email
- Automated service reminders, review requests, and live chat
- Online and in-person payment processing
- VIN-level NHTSA recall checks with auto-generated customer notification language

### Reporting, Multi-Location & Fleet

- Real-time KPI dashboards (revenue, car count, ARO, gross profit, technician hours)
- Multi-location support with centralised reporting and team management
- QuickBooks Online integration for accounting sync
- Fleet-specific features for bulk operations and maintenance scheduling

---

## AI-Native Advantage

AI is applied where incumbents still rely on manual entry or static rules. Repair orders can be drafted from DTC codes and symptom descriptions, with suggested probable causes, applicable TSBs, and labour operation codes. Computer vision interprets inspection photos to flag wear and surface upsell opportunities. Time-series forecasting predicts parts consumption from vehicle demographics, while NLP-driven coaching identifies technician training gaps from repair patterns. VIN-level recall and TSB monitoring run automatically at check-in.

---

## Tech Stack & Deployment

A cloud-native architecture is the expected primary deployment mode, matching the direction of the category, with mobile-first technician interfaces. Integration surfaces include OEM parts catalogues, telematics feeds, NHTSA recall databases, QuickBooks Online, and PCI-compliant payment processors (typically via integrated terminals to reduce PCI scope). The platform should align with industry standards including ASE certification tracking, OSHA 29 CFR 1910 recordkeeping, EPA / RCRA hazardous waste tracking, Motorist Assurance Program (MAP) inspection standards, NHTSA recall compliance, and PCI DSS for payments.

---

## Market Context

The broad auto repair software market was valued at approximately USD 34.32 billion in 2026, projected to reach USD 57.19 billion by 2030 at a 13.6% CAGR; a narrower shop management software definition puts the 2026 market at USD 3.4 billion, growing to USD 8.6 billion by 2033 at 14.2% CAGR (Market Research Future; Research and Markets). Entry-level incumbent pricing sits around USD 104/month, with Garage360 cited as an affordable option at USD 79/month. Primary buyers are independent single- and multi-bay shops, multi-location operators, and fleet service centres; over 60% of shops are expected to use some form of AI by late 2026.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
