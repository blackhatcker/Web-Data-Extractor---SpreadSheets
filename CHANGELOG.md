Changelog
All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog, and this project adheres to Semantic Versioning.

Unreleased
1.1.0 - 2026-04-03

Changed
Output format changed from XML to XLSX (Excel)
Each extracted table is now a separate named sheet in the workbook
Optional "Metadata" sheet with page URL, title, description, and extraction timestamp
Numeric cell values are now stored as numbers in Excel (not text) for correct sorting and formula support
Column auto-filters applied to all header rows automatically

Removed
XML output and XML preview panel

1.0.0 - 2026-04-02

Added
Initial release of Web Data Extractor
URL input with placeholder pointing to a CISA vulnerability bulletin as a usage example
Preview mode: shows table schema (headers, row/column counts, captions) before extraction
Extract mode: fetches the page server-side and parses all HTML tables
XML output with structured extraction results
"Include Headers" and "Include Metadata" toggle options
Comprehensive error handling:
Invalid or non-HTTP URLs
HTTP 403 (access denied), 404 (not found), 429 (rate limited), 5xx (server errors)
15-second fetch timeout
Unsupported content types
Pages with no HTML tables
React + Vite frontend with shadcn/ui components
Express 5 API backend with OpenAPI 3.1 spec and Orval codegen
pnpm monorepo structure
