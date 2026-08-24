HubSpot

<aside>

ℹ️ This guide provides step-by-step instructions for configuring Hubspot in different privacy configurations and how these configurations must be reflected in the Consenter Manager when configuring your Consent Banner.

**Step 1:** Choose which configuration matches your demands and configure Hubspot accordingly 

**Step 2:**  Configure the Consent Banner in the Consenter Manager accordingly

**Step 3:** Explain how you use the third party provider in your **privacy policy**

</aside>

# Hubspot Configuration Guide

HubSpot is a CRM and marketing platform that deploys a JavaScript tracking code on customer websites to collect visitor behaviour, session data, and contact information. Depending on configuration, HubSpot can operate as a lightweight analytics tool or a comprehensive contact identification and advertising platform. The configurations below cover the most privacy-relevant settings and their corresponding mappings in the Customer Panel (CP).

---

## Step 1 — HubSpot Configuration

| # | Configuration Area | Where in HubSpot | Configuration A — Low Risk | Configuration B — Medium Risk | Configuration C — Higher Risk |
| --- | --- | --- | --- | --- | --- |
| 1 | Consent & tracking activation | Settings → Privacy & Consent → Cookie Tracking | Require consent before tracking script fires | Require consent before tracking script fires | Require consent before tracking script fires |
| 2 | IP anonymisation | Settings → Privacy & Consent → Privacy Settings | Enabled (last octet masked) | Enabled (last octet masked) | Disabled (full IP collected) |
| 3 | Contact identification | Settings → Tracking & Analytics → Tracking Code; Marketing → Forms | Disabled — anonymous sessions only | Enabled via form submissions only (name, email) | Enabled — forms, email link tracking (`_hsenc` token), and/or Identify API |
| 4 | Advertising integrations | Marketing → Ads | None connected | None connected | Google Ads, Meta Ads, and/or LinkedIn Ads connected; Google Consent Mode v2 active |
| 5 | Data retention | Settings → Privacy & Consent → Data Retention | 6 months | 13 months | 25 months (platform maximum) |
| 6 | Processing location | Account settings / HubSpot subscription tier | EU Data Residency (Enterprise tier); potential US government access via CLOUD Act | EU Data Residency (Enterprise tier); potential US government access via CLOUD Act | US-based (default); SCCs available; US government access via CLOUD Act |

### Configuration A — Low Risk

Use this configuration when HubSpot is used solely for anonymous website analytics. Consent is required before the tracking script fires. IP anonymisation is enabled, so only a masked IP address is collected. No contact identification is in use — visitors are tracked as anonymous sessions via first-party cookies (`hubspotutk`, `__hstc`) scoped to the website domain. No advertising integrations are connected. Data is retained for 6 months and, where possible, stored within the EU using HubSpot's EU Data Residency option (Enterprise tier). However, as HubSpot Inc. is a US-based enterprise, data stored in the EU remains potentially subject to access by US government authorities under the CLOUD Act, irrespective of the storage location. This should be disclosed as a potential US data transfer in the consent banner. HubSpot acts as a data processor; a DPA is incorporated into HubSpot's Customer Terms of Service and available at legal.hubspot.com.

### Configuration B — Medium Risk

Use this configuration when HubSpot is used for website analytics combined with lead capture via HubSpot forms. Consent is required before the tracking script fires. IP anonymisation is enabled. Visitors who submit a form (e.g. a contact or newsletter sign-up form) are identified by their submitted details (name, email address), and HubSpot creates a contact record linked to their session cookie. No email link tracking (`_hsenc`) or Identify API is in use. No advertising integrations are connected. Data is retained for 13 months and stored within the EU where possible. However, as HubSpot Inc. is a US-based enterprise, data stored in the EU remains potentially subject to access by US government authorities under the CLOUD Act, irrespective of the storage location. This should be disclosed as a potential US data transfer in the consent banner. HubSpot acts as a data processor under its standard DPA.

### Configuration C — Higher Risk

Use this configuration when HubSpot is used for full CRM-integrated tracking including contact identification through multiple channels and connected advertising platforms. Consent is required before the tracking script fires. IP anonymisation is disabled, so the full IP address is collected. Visitors are identified via one or more of the following: form submissions, the `_hsenc` contact token appended to email links (which links individual clicks back to a known contact record), or the HubSpot Identify API (which explicitly associates a visitor's cookie session with a known contact). One or more ad platforms (Google Ads, Meta Ads, LinkedIn Ads) are connected via Marketing → Ads, and Google Consent Mode v2 is activated to pass consent signals to Google. Each connected ad platform deploys its own third-party tracking pixel alongside the HubSpot script. Data is retained for 25 months. Default HubSpot accounts store data in the US; Standard Contractual Clauses (SCCs) are included in HubSpot's DPA. Even where EU Data Residency is active, HubSpot Inc. as a US-based enterprise remains subject to the CLOUD Act, meaning US government authorities may access data regardless of storage location. Both the default US hosting and the CLOUD Act risk should be disclosed as US data transfers in the consent banner. HubSpot acts as a data processor for its own processing; each connected ad platform operates as an Independent Controller under its own terms and must be configured as a separate entry in the Customer Panel.

---

## Step 2 — Mapping in the Customer Panel

Using the HubSpot configurations defined in Step 1, apply the following mappings in the Customer Panel to ensure the consent banner correctly reflects the data processing activities.

### 2.1 Configuration A — Low Risk

| **Customer Panel Setting** | **Value to Select** |
| --- | --- |
| Tracking method | First party tracking (cross-session) |
| Identifier | Device identifiers |
| Data categories | Aggregated site statistics, Browsing and interaction data, Device characteristics, Device identifiers, IP address anonymised, Non-precise location data |
| Legal role of data recipient | Processor |
| Personalisation model | No personalisation |
| Maximum storage duration | 6 months |
| Processing location | EU (if EU Data Residency is active) / US (potential access via CLOUD Act) |

### 2.2 Configuration B — Medium Risk

| **Customer Panel Setting** | **Value to Select** |
| --- | --- |
| Tracking method | First party tracking (cross-session) |
| Identifier | Device identifiers, Direct identifier |
| Data categories | Aggregated site statistics, Browsing and interaction data, Device characteristics, Device identifiers, IP address anonymised, Non-precise location data, Direct identifier, User-provided data, Users' profiles |
| Legal role of data recipient | Processor |
| Personalisation model | Group based (behaviour) |
| Maximum storage duration | 13 months |
| Processing location | EU (if EU Data Residency is active) / US (potential access via CLOUD Act) |

### 2.3 Configuration C — Higher Risk

This configuration requires a separate Customer Panel entry for each connected advertising platform, as these operate as Independent Controllers.

**HubSpot (Processor entry):**

| **Customer Panel Setting** | **Value to Select** |
| --- | --- |
| Tracking method | Third party tracking (cross-session, cross-website) |
| Identifier | Device identifiers, Authentication-derived identifiers, Direct identifier |
| Data categories | Aggregated site statistics, Browsing and interaction data, Device characteristics, Device identifiers, IP address, Non-precise location data, Authentication-derived identifiers, Direct identifier, Users' profiles, Privacy choices (if Google Consent Mode v2 active), e-commerce Activity (if revenue tracking enabled) |
| Legal role of data recipient | Processor |
| Personalisation model | Profile based |
| Maximum storage duration | 25 months |
| Processing location | US (default) with SCCs / EU (if EU Data Residency active); US government access via CLOUD Act applies in all cases |

**Connected Ad Platforms — configure a separate entry for each (e.g. Google Ads, Meta Ads, LinkedIn Ads):**

| **Customer Panel Setting** | **Value to Select** |
| --- | --- |
| Tracking method | Third party tracking (cross-session, cross-website) |
| Identifier | Device identifiers |
| Data categories | Browsing and interaction data, Device identifiers, Privacy choices (Google Consent Mode v2), Users' profiles |
| Legal role of data recipient | Individual Controller |
| Personalisation model | Profile based |

> **Note:** Advertising platforms such as Google Ads, Meta Ads, and LinkedIn Ads operate as Independent Controllers under their own terms. Each platform must be listed as a separate data recipient in the Customer Panel, and the consent banner must surface appropriate information about data sharing with each platform individually.
>