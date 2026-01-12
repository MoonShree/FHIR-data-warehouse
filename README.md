### The Container Advantage

Docker eliminated dependency conflicts across different student laptops by packaging the FHIR server and all required libraries into a single container image. This ensured everyone ran the exact same environment regardless of OS or hardware, removing “it works on my machine” problems and making setup reproducible and consistent.

### Semantic Integrity

The project removed unreliable “magic strings” from the RMHC CSV (such as M/F and local abbreviations) by defining a ConceptMap and using the FHIR `$translate` operation. This ensured source values were converted into standardized codes with clear meaning, preserving clinical semantics and enabling true interoperability.

### Transactional Atomicity

Patient and Observation resources were uploaded using FHIR **Transaction Bundles** instead of separate requests. By linking them with temporary UUIDs and committing them in a single operation, either all resources were created or none were. This prevented partial saves and eliminated orphaned clinical data, ensuring referential integrity.
