# Entity Versioning Guidelines

## Introduction

This document outlines the guidelines for versioning entities in YAML definitions. Versioning entities helps in managing changes to the structure and properties of entities over time while maintaining compatibility with existing data and systems.

## Versioning Rules

1. **Semantic Versioning**: Entities should follow the Semantic Versioning (SemVer) scheme for versioning.
    - Version numbers should follow the format `MAJOR.MINOR.PATCH`.
    - Increment the:
        - MAJOR version for incompatible changes (e.g., changes that break existing data or systems).
        - MINOR version for backward-compatible additions (e.g., adding new properties or attributes).
        - PATCH version for backward-compatible bug fixes (e.g., fixing validation errors).
    - Examples:
        - `1.0.0` (Initial version)
        - `1.1.0` (Adding a new property)
        - `2.0.0` (Incompatible changes)

2. **Backward Compatibility**: Changes to entities should strive to maintain backward compatibility whenever possible.
    - Adding new properties or attributes should not break existing data or systems.
    - Modifying existing properties or attributes should be done carefully to avoid disrupting existing functionality.

3. **Deprecation**: When deprecating properties or attributes, provide clear documentation about the deprecation and its replacement, if applicable. Deprecated properties should be phased out over time.

4. **Documentation**: Maintain clear and up-to-date documentation for each version of the entity, highlighting any changes or updates made in each version. 

## Example

Consider an example of versioning the "Sample" entity:

```yaml
Sample:
  description: >
    A dataset containing information about a biological sample, including sample ID, type, preservation method, site of resection or biopsy, and tissue type.
  properties:
    sampleId:
      description: >
        Identifier for the sample. Example: "SAMPLE123".
      type: string
    type:
      description: >
        Type of the sample, such as blood, tissue, or fluid. Example: "Tissue".
      type: string
    preservationMethod:
      description: >
        Method used for preserving the sample, such as freezing or fixation. Example: "Frozen".
      type: string
    siteOfResectionOrBiopsy:
      description: >
        Site of resection or biopsy where the sample was obtained from. Example: "Lung".
      type: string
    tissueType:
      description: >
        Type of tissue represented by the sample, such as epithelial or connective tissue. Example: "Epithelial".
      type: string
  type: object
  version: 1.0.0
```

## Versioning Examples:
1. **Patch Version Increment (0.0.1)**:
    - Description: Fixing a validation error in the "tissueType" property.
    - Implication: No changes to existing properties or their meanings.

2. **Minor Version Increment (0.1.0)**:

    - Description: Adding a new property "collectionDate" to capture the date of sample collection.
    - Implication: Backward-compatible addition, existing data structures remain unaffected.

3. **Major Version Increment (1.0.0)**:

    - Description: Removing the "preservationMethod" property and replacing it with "storageCondition".
    - Implication: Incompatible change, existing data structures need to be updated to accommodate the new property.

Following these versioning examples ensures consistency in version increments based on the type of changes made to the entity.