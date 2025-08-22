# Copilot Workspace Instructions — Schema.org JSON-LD (Workspace Guide)

This file gives Copilot concise, practical guardrails for this repo. The canonical, exhaustive rules live in `.github/instructions/schema.instructions.md`. If anything here conflicts with the canonical spec, the canonical spec wins.

## What to Follow (Essentials)
- Use JSON-LD only with "@context": "https://schema.org".
- Zero guessing: only include properties/values present in source content; ask for missing required data.
- Validate to zero errors in https://validator.schema.org/ before delivering output. Use Google Rich Results Test when applicable.
- Choose the most-specific applicable Schema.org type; avoid deprecated or pending types.
- Enforce exact value ranges (Text, URL, Number, Boolean, Date/DateTime, Enumeration). Use absolute HTTPS URLs.
- Prefer `hasCertification` (`Certification`) for regulatory status; keep `hasCredential` only for legacy/educational contexts.
- Replace placeholders before shipping output. Never ship `{{...}}` in final JSON.

## Parameterization (Location-Agnostic)
Use placeholders to keep prompts reusable across locations:
- `{{streetAddress}}`, `{{city}}`, `{{administrativeArea}}`, `{{postalCode}}`, `{{country}}`
- `{{latitude}}`, `{{longitude}}`, `{{geoRadiusMeters}}`
Guidance:
- Avoid hard-coding city names in `name`/`description` unless provided.
- For `areaServed`, combine `City` + `AdministrativeArea`; optionally add a `GeoCircle` with meter-based radius.

## Quick Workflows (Recipes)
- Validate a file
  - "Validate `LocalBusiness-registredAgent.json` against Schema.org; list required/recommended gaps and datatype issues; produce a corrected JSON-LD that passes validator.schema.org with zero errors."
- Generate LocalBusiness for a new location
  - "Create `LocalBusiness` JSON-LD for `{{streetAddress}}`, `{{city}}`, `{{administrativeArea}}`, `{{postalCode}}` (and `{{latitude}}`, `{{longitude}}` if available), mirroring structural patterns in `LocalBusiness-registredAgent.json` (contactPoint, areaServed City+AdministrativeArea+GeoCircle, makesOffer serviceOutput, potentialAction EntryPoint, hasCertification). Validate with zero errors."
- Review offers/services
  - "Review `makesOffer` entries for correct typing (`Service`/`ParcelDelivery`/`DigitalDocument`/`Product`), value ranges, and completeness; fix issues and revalidate."
- Tighten credentials
  - "Prefer `hasCertification`; ensure `certificationIdentification`, `certificationStatus`, and `issuedBy` are present and valid."

## SEO & AI Search (Keep it honest)
- Use descriptive, specific service text; avoid keyword stuffing and repeated city names.
- Bind entity to page via `@id` and `mainEntityOfPage` with canonical URL.
- Include only official social/profile links in `sameAs`.
- Use `serviceOutput` to enumerate concrete deliverables (e.g., `DigitalDocument`, `ParcelDelivery`, `Product`, `Service`).

## Where Things Go
- Canonical rules, algorithms, and property details: `.github/instructions/schema.instructions.md` (and reference artifacts in the same folder).
- This concise guide: `.vscode/copilot-instructions.md`.
- Runnable prompt files: `.vscode/prompts/*.prompt.md` (these appear in Copilot Chat’s Workspace Prompts). Avoid using draft folders for live prompts.

## Reference
- Exemplar: `LocalBusiness-registredAgent.json` (use as a pattern; do not hard-code cities).
- Validators/utilities: `src/validate/`.
