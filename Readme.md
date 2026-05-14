Enterprise SAML SSO Sandbox

A lightweight, containerised SAML 2.0 Service Provider (SP) built with Flask and python3-saml, designed for hands-on learning, testing, and troubleshooting of enterprise federation using Microsoft Entra ID.

This project focuses on visibility, clarity, and real-world authentication behaviour rather than production abstraction. The goal is to provide a SAML environment that engineers can actually inspect, understand, and extend.

Overview

This sandbox demonstrates a complete enterprise SAML authentication flow using Microsoft Entra ID as the Identity Provider (IdP).

It provides a safe environment for:

Understanding SAML authentication end-to-end
Inspecting real SAML assertions and claims
Exploring session handling and federation behaviour
Testing group-to-role mapping concepts
Troubleshooting enterprise SSO integrations

The application includes a modern dark-themed UI and claims inspection portal designed to make identity flows easier to visualise and debug.

Architecture
Core Components
Component	Technology
Framework	Flask
SAML Library	python3-saml (OneLogin)
Identity Provider	Microsoft Entra ID
Container Platform	Docker
Reverse Proxy Support	NGINX / Cloudflare Compatible
Authentication Flow
User
  ↓
Flask SAML Service Provider
  ↓
Microsoft Entra ID
  ↓
SAML Assertion
  ↓
Claims & Session Inspection

The application operates as a SAML Service Provider (SP) and supports SP-initiated authentication flows.

Key Features
Enterprise SAML Authentication
SP-initiated SAML login
Assertion Consumer Service (/acs)
Session handling and inspection
Entra ID federation integration
Claims Inspection Portal

The Claims page provides visibility into:

NameID
Session Index
Login timestamp
Raw SAML claims
Group memberships
Derived application roles
Certificate validation visibility (debug mode)

This makes it easy to inspect how Entra ID issues identity assertions in real-world federation scenarios.

Group → Role Mapping

Supports mapping Entra group Object IDs to internal application roles.

Designed to:

remain simple
be easy to extend
safely handle users without assigned groups
Runtime Debug Mode

Debug visibility can be toggled directly from the UI without restarting the application.

Useful for:

troubleshooting federation issues
inspecting claims
validating certificate behaviour
observing session state
Logout Support
Local Logout
Clears the Flask session safely
Always available regardless of IdP state
Federated Logout (SLO)
Supports SAML Single Logout
Gracefully handles IdP logout failures
Prevents session-breaking logout loops
UI & Design

The application includes a lightweight dark-themed interface focused on readability and observability.

The UI was intentionally designed to:

simplify federation testing
improve claim visibility
provide a cleaner troubleshooting experience
separate enterprise SSO testing from social federation experiments
Environment-Driven Configuration

Sensitive values are injected through environment variables:

Flask secret key
Entra Entity ID
SAML SSO URL
IdP signing certificate

This keeps secrets out of source control and simplifies container deployments.

Containerisation

The project ships with:

Dockerfile
docker-compose configuration
GitHub Actions CI/CD support
Docker Hub deployment workflow

This enables rapid testing and portable deployments across environments.

Intended Usage

This project is ideal for:

SAML learning labs
Enterprise SSO troubleshooting
Identity and federation testing
Entra ID experimentation
Claims analysis
Portfolio / demonstration environments

It is intentionally designed as an engineering sandbox rather than a production-ready identity platform.

Open Source

This project is open source and intended for collaborative learning and experimentation.

Contributions are welcome, including:

UI improvements
federation enhancements
troubleshooting tools
additional observability features
Roadmap

Planned future enhancements include:

Metadata endpoint (/metadata)
Signed SAML requests
Expanded role-based access controls
Enhanced federation diagnostics
Improved certificate lifecycle visibility
Additional UI refinements
Related Project

A separate companion project is being developed for:

Federated Social Login Sandbox

This environment focuses on:

Google federation
Facebook federation
Apple ID federation
Entra External ID (CIAM)
OAuth/OpenID Connect identity brokering

The two projects are intentionally separated to maintain clean architectural boundaries between enterprise SAML federation and consumer/social identity flows.

Version

Current Release:

v1.1