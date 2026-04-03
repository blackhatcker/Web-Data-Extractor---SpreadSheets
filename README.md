Web Data Extractor
A tool for extracting structured table data from any webpage and exporting it as an Excel (XLSX) file.

Built by Lyon & Fiurex LLC Group.

Overview
Web Data Extractor lets you paste any webpage URL, instantly preview the tables found on that page, and download the full dataset as a formatted Excel workbook. Each HTML table becomes its own named sheet, with column auto-filters applied and numeric values properly typed.

Key Features
Preview mode — see a schema summary (table count, column headers, row counts) before committing to a full extraction
XLSX export — each table becomes a separate sheet in a well-formatted Excel workbook
Metadata sheet — optional sheet with page URL, title, description, and extraction timestamp
Numeric typing — numeric cell values are stored as numbers in Excel, not text
Auto-filters — column filters applied to every header row automatically
Comprehensive error handling — clear messages for invalid URLs, blocked pages (403), missing pages (404), rate limits (429), timeouts, and pages with no tables

Tech Stack
Layer	Technology
Frontend	React 19, Vite 7, TypeScript, Tailwind CSS, shadcn/ui
Backend	Node.js 24, Express 5, TypeScript
XLSX generation	SheetJS (xlsx)
HTML parsing	node-html-parser
API contract	OpenAPI 3.1, Orval codegen
Monorepo	pnpm workspaces


Getting Started
Prerequisites
Node.js v24+
pnpm v10+

Installation
git clone https://github.com/your-org/web-data-extractor.git
cd web-data-extractor
pnpm install

Running locally
Start the API server:

pnpm --filter @workspace/api-server run dev
Start the frontend:

pnpm --filter @workspace/web-extractor run dev
The app will be available at http://localhost:<PORT> (port assigned automatically).

Regenerating the API client
After changing lib/api-spec/openapi.yaml:

pnpm --filter @workspace/api-spec run codegen
Building for production
pnpm run build

.
├── artifacts/
│   ├── api-server/          # Express 5 API server
│   │   └── src/
│   │       ├── lib/
│   │       │   └── extractor.ts    # Fetch, parse, XLSX build logic
│   │       └── routes/
│   │           └── extract.ts      # /api/extract, /api/extract/preview
│   └── web-extractor/       # React + Vite frontend
│       └── src/
│           └── pages/
│               └── home.tsx        # Main extractor UI
├── lib/
│   ├── api-spec/            # OpenAPI 3.1 spec + Orval config
│   ├── api-client-react/    # Generated React Query hooks
│   └── api-zod/             # Generated Zod validation schemas
└── scripts/                 # Shared utility scripts


API Reference
POST /api/extract/preview
Preview tables found on a webpage without downloading.

Request body:

{
  "url": "https://example.com/page-with-tables",
  "includeHeaders": true,
  "includeMetadata": true
}
Response:

{
  "pageTitle": "Example Page",
  "pageDescription": "...",
  "url": "https://example.com/page-with-tables",
  "tables": [
    {
      "index": 0,
      "headers": ["Column A", "Column B"],
      "rowCount": 42,
      "columnCount": 2,
      "caption": "Optional table caption"
    }
  ],
  "totalRows": 42
}
POST /api/extract
Extract all tables and return a base64-encoded XLSX file.

Request body: same as /preview

Response:

{
  "xlsxBase64": "<base64-encoded .xlsx file>",
  "pageTitle": "Example Page",
  "tableCount": 1,
  "rowCount": 42,
  "url": "https://example.com/page-with-tables",
  "extractedAt": "2026-04-03T00:00:00.000Z"
}

Error Codes
Code	Meaning
INVALID_REQUEST	Malformed request body
FETCH_FAILED	Could not fetch the URL (network error, timeout, 4xx/5xx)
PARSE_FAILED	Could not parse the page HTML
NO_TABLES	Page was fetched successfully but contains no HTML tables
XLSX_BUILD_FAILED	Internal error building the XLSX file

Contributing
See CONTRIBUTING.md for guidelines.

Security
See SECURITY.md for the vulnerability reporting policy.

License
MIT © Lyon & Fiurex LLC Group





