# CALM Standards

This directory contains company-specific CALM (Common Architecture Language Model) standards that extend the core CALM definitions with additional properties required for our organization's governance and compliance needs.

## What are CALM Standards?

CALM Standards are JSON Schema files that extend the core CALM v1.2 definitions using schema composition. They allow organizations to enforce additional metadata requirements on architecture models while maintaining compatibility with the core CALM specification.

### How Standards Extend CALM

Standards use the `allOf` JSON Schema composition keyword to combine:

1. **Core CALM Definition**: Referenced via `$ref` to the official CALM schema (e.g., `https://calm.finos.org/release/1.2/meta/calm.json#/defs/node`)

2. **Additional Properties**: Custom properties specific to organizational requirements

The `additionalProperties: true` setting ensures that any properties from the core CALM definition are still allowed, while the `required` array enforces the additional properties.

Example structure:
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "allOf": [
    {
      "$ref": "https://calm.finos.org/release/1.2/meta/calm.json#/defs/node"
    },
    {
      "type": "object",
      "properties": {
        // Custom properties here
      },
      "required": ["customProperty"],
      "additionalProperties": true
    }
  ]
}
```

## Company Node Standard

Located in: `company-node-standard.json`

This standard extends the core CALM node definition with properties required for financial tracking, ownership, and environment classification.

### Required Properties

- **costCenter** (string, required): Company cost center code in the format `CC-XXXX` where `XXXX` are exactly 4 digits (e.g., `CC-1234`). Used for financial tracking and resource allocation.

- **owner** (string, required): Team or individual responsible for the node. Should include contact information or team name for operational support and maintenance.

- **environment** (string, required): Deployment environment classification. Must be one of:
  - `development`: For active development environments
  - `staging`: For pre-production testing
  - `production`: For live customer-facing systems

## Company Relationship Standard

Located in: `company-relationship-standard.json`

This standard extends the core CALM relationship definition with properties required for data governance and security classification.

### Required Properties

- **dataClassification** (string, required): Classification level of data flowing through this relationship. Must be one of:
  - `public`: For openly accessible data
  - `internal`: For company-only data
  - `confidential`: For sensitive business data
  - `restricted`: For highly sensitive or regulated data

- **encrypted** (boolean, required): Indicates whether the connection between nodes is encrypted. Should be `true` for any relationship carrying sensitive data or traversing untrusted networks.

## Usage

These standards can be referenced in architecture validation tools and documentation generation to ensure compliance with company policies. When creating or updating CALM architecture models, ensure all nodes and relationships conform to these standards.