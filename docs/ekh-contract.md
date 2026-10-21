# EKH Contract v0.1 (proposal)

EKH is a **model- and agent-independent organizational asset contract**, not a replacement for MCP, Git, artifact repositories or workflow engines.

**Principle:** discover once, publish through SDLC, reuse across authorized employees, applications and AI agents.

## Universal asset envelope

- **Identity:** stable ID, name, version, owner, type
- **Discovery:** description, intent phrases, tags
- **Access:** classification and required scopes
- **Interface:** input/output JSON Schemas for invocable assets, or a source reference for knowledge/data assets
- **Backing systems:** invocation binding, source revision and dependencies
- **Lifecycle:** candidate, validated, approved, deprecated or retired; actual status must come from enterprise release control

Asset types can include `knowledge`, `data`, `tool`, `workflow`, `artifact` and `service`. Only invocable types require execution contracts.

## Proposed operations

| Operation | Purpose |
| --- | --- |
| `ekh.discover` | Search available assets by intent and filters, respecting authorization |
| `ekh.describe` | Fetch a versioned descriptor and interface |
| `ekh.resolve` | Obtain an authorized source reference for non-executable assets |
| `ekh.invoke` | Execute an approved capability; return result or asynchronous job ID |
| `ekh.publish` | Submit a candidate manifest to existing SDLC gates; never auto-approve |
| `ekh.status` | Read candidate/release lifecycle state |

## Hit / miss integration

```text
Request -> EKH discovery
  HIT  -> access check -> invoke existing workflow / resolve existing asset -> result
  MISS -> agent reasons -> generate candidate asset -> Git -> CI -> security/compliance
       -> Artifactory -> CD -> validation -> release -> EKH publication
```

An EKH miss **does not automatically publish agent output**. Validation and approval remain with established SDLC systems. Existing storage and execution platforms remain authoritative.

## Example

See [simulation-report.yaml](../examples/ekh/simulation-report.yaml), a proposed EKH manifest showing workflow discovery metadata, JSON Schema inputs/outputs, MCP invocation binding, source revision, dependencies and validation reference.

**Status:** conceptual v0.1 example, not a deployed standard, live integration, or proof of approval.
