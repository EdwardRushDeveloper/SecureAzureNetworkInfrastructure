<!--
Sync Impact Report:
- Version change: none → 1.0.0
- List of modified principles: All principles added (BICEP-First Infrastructure, Modular Component Architecture, Compilation Validation (No Unit Tests), Parameter Configuration Files, Centralized Settings Management)
- Added sections: Core Principles (5), Infrastructure Standards, Development Workflow
- Removed sections: None
- Templates requiring updates: None (templates are general and do not conflict)
- Follow-up TODOs: None
-->
# Secure Azure Network Infrastructure Constitution

## Core Principles

### I. BICEP-First Infrastructure
All Azure infrastructure MUST be defined in BICEP language, not Azure Resource Manager (ARM) JSON templates. BICEP provides superior readability and maintainability.

### II. Modular Component Architecture
All infrastructure components MUST be designed as reusable, independently deployable modules. Each module must encapsulate a single concern and be versioned separately.

### III. Compilation Validation (No Unit Tests)
Unit tests are not feasible for infrastructure code. Instead, BICEP file compilation and build validation MUST be used to ensure all components compile successfully before deployment.

### IV. Parameter Configuration Files
All infrastructure settings MUST be defined in parameter.json files that are separate from BICEP templates. Parameters drive all environment-specific and configurable values.

### V. Centralized Settings Management
A single source Settings file (settings.json) MUST be used to pass through all modularized components instead of individual parameter values. BICEP properties MUST be represented as JSON nodes in the Settings file so entire JSON objects can be assigned to modularized components, eliminating the need to access individual property settings from the JSON file.

## Infrastructure Standards

### BICEP Compliance Rules
- All new infrastructure code MUST be written in BICEP syntax only.
- Existing ARM templates MUST be converted to BICEP during refactoring.
- BICEP files MUST follow official formatting standards and best practices.
- Compilation errors MUST be resolved before any deployment.

### Settings Management Rules
- The settings.json file MUST be the single source of truth for all configuration.
- Parameter.json files MUST reference values from settings.json where possible.
- Changes to settings MUST be validated for impact on all dependent modules.
- Settings MUST be environment-specific and version-controlled.

### Deployment Validation Rules
- All BICEP files MUST compile successfully before deployment.
- Build pipelines MUST include BICEP compilation checks.
- Deployment MUST fail if any module compilation fails.
- Validation MUST occur in CI/CD pipelines before staging deployments.

## Development Workflow

### Code Review Requirements
- All BICEP changes MUST be reviewed for compliance with BICEP-First principle.
- Module boundaries MUST be validated during review.
- Settings changes MUST be reviewed for consistency across modules.
- Compilation validation MUST be part of the review process.

### Quality Gates
- BICEP compilation MUST pass in all environments.
- Settings validation MUST occur before deployment.
- Module versioning MUST follow semantic versioning.
- Deployment MUST be blocked if any quality gate fails.

## Governance

Constitution supersedes all other practices. Amendments require documentation, approval, and migration plan.

All PRs/reviews must verify compliance with BICEP-First, Modular Architecture, and Settings Management principles. Complexity must be justified. Use constitution for runtime development guidance.

**Version**: 1.0.0 | **Ratified**: 2026-03-20 | **Last Amended**: 2026-03-20
