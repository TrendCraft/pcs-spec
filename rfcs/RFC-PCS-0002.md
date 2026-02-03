RFC-PCS-0002

Cognitive State Types and Registries
Status: Draft
Intended Status: Standards Track
Updates: RFC-PCS-0001
Expires: TBD

1. Abstract
This document defines the Cognitive State Types and associated registries used by systems conforming to the Persistra Cognitive Standard (PCS).

Cognitive State Types provide a structured, interoperable vocabulary for representing persistent cognition, including decisions, policies, constraints, identity, and provenance.

Registries defined herein enable extensibility while preserving semantic stability across implementations.

2. Motivation
Persistent cognition requires more than storage. It requires semantic agreement on what is being stored, why it matters, and how it must be enforced.

Without standardized cognitive state types:
Systems cannot reliably interoperate
Cognitive continuity degrades across vendors
Policy enforcement becomes ambiguous
Certification and compliance are unverifiable

PCS registries establish a shared cognitive vocabulary analogous to MIME types, OAuth scopes, or POSIX resource classes.

3. Design Principles
Cognitive State Types and Registries adhere to the following principles:
Minimal Core, Extensible Edge
Semantic Stability Across Versions
Model-Agnostic Representation
Deterministic Interpretation
Auditability and Provenance Preservation

4. Cognitive State Type Overview
All PCS-compliant systems MUST represent persistent cognition using one or more Cognitive State Records (CSRs).

Each CSR consists of:
A record_type
A unique identifier
Structured payload
Metadata (timestamps, provenance)
Enforcement semantics (where applicable)

5. Core Cognitive State Types
The following core record types are REQUIRED for PCS compliance.
5.1 Decision Record (decision_record)

Represents an immutable architectural, design, or operational decision.

Use cases:
Architectural constraints
Technology selections
Non-reversible choices
Required properties:
decision_id
decision_statement
decision_scope
timestamp
author
immutability_flag

Decision Records MUST NOT be modified after creation.

5.2 Policy Record (policy_record)
Represents enforceable constraints governing system behavior.

Use cases:
Security restrictions
Budget caps
Compliance requirements
Required properties:
policy_id
policy_category
policy_rules
enforcement_level
violation_response

Policy Records MUST be evaluated deterministically prior to output emission.

5.3 Vision Anchor (vision_anchor)
Represents long-lived intent or guiding principles that MUST persist across sessions.

Use cases:
System goals
Design philosophy
Mission constraints
Required properties:
anchor_id
anchor_type
anchor_statement
priority_level

Vision Anchors MAY override transient contextual inputs.

5.4 Identity Context (identity_context)
Represents identity-scoped cognitive state.

Use cases:
User preferences
Role-based behavior
Permission boundaries
Required properties:
identity_id
identity_type
permission_scope
contextual_attributes

5.5 Provenance Record (provenance_record)
Represents traceability and audit metadata.

Use cases:
Compliance audits
Forensic analysis
Decision lineage
Required properties:
source_record_ids
generation_method
model_context
timestamp

6. Registry Architecture
PCS defines authoritative registries for enumerated cognitive concepts.
Registries ensure interoperability and prevent semantic fragmentation.

7. Defined Registries

7.1 Record Type Registry
Defines valid record_type values.
Initial registry entries:
decision_record
policy_record
vision_anchor
identity_context
provenance_record

7.2 Policy Category Registry
Defines standardized policy domains.
Initial entries:
security
compliance
budget
safety
governance

7.3 Violation Type Registry
Defines standardized violation semantics.

Initial entries:
forbidden_technology
policy_conflict
budget_exceeded
compliance_violation
permission_denied

7.4 Anchor Type Registry
Defines categories of long-lived intent.

Initial entries:
architectural
security
mission
ethical
operational

8. Registry Governance

Registries MUST be:
Publicly readable
Versioned
Append-only (no deletion of existing entries)

New registry entries MAY be proposed by implementers.
Registry modification policies are outside the scope of this document.

9. Extensibility
Implementations MAY define private or experimental record types, provided:
They do not conflict with registered types
They are clearly namespaced
They do not alter PCS invariants

Private extensions MUST NOT be represented as PCS-certified types.

10. Versioning and Compatibility
Cognitive State Types MUST remain backward compatible.
Deprecated types MAY be marked as such but MUST remain interpretable.
Breaking changes require a new major PCS version.

11. Security Considerations
Improper handling of cognitive state types may result in:
Policy bypass
Identity leakage
Decision corruption

Implementations SHOULD protect registries and records using appropriate cryptographic and access controls.

12. Relationship to Intellectual Property
Certain implementations of Cognitive State Types and registries may be covered by existing or pending intellectual property rights.

This document does not grant any license to such rights.

13. IANA Considerations
This document defines registries analogous to IANA-managed registries but does not request IANA action.

Registry stewardship is defined outside the scope of this specification.

14. Conclusion
Standardized Cognitive State Types and Registries provide the semantic foundation for persistent AI cognition.

By defining a shared vocabulary, PCS enables interoperability, auditability, and governance across AI systems without constraining model innovation.

End of RFC-PCS-0002