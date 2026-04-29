# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Single-file HTML app (`recetario.html`) for generating medical prescriptions as PDF. No build step, no dependencies to install — open the file directly in a browser.

## Architecture

Everything lives in one file: CSS custom properties (`:root`), HTML structure, and vanilla JS. There is no framework, bundler, or package manager.

**External dependencies (CDN only):**
- [jsPDF 2.5.1](https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js) — PDF generation
- Google Fonts — Playfair Display (headings/Rx symbol), Source Sans 3 (body)

## Key details

- **PDF format:** half-letter / media carta — 139.7 × 215.9 mm (hardcoded in `generarPDF()`)
- **Prescription limit:** 10 lines max (enforced by `rxCount >= 10` guard in `addLine()`)
- **Doctor info** is hardcoded in two places: the visible HTML header and inside `generarPDF()` (footer strings referencing "Dra. Maribel Ornelas" and the placeholder address/phone). When updating doctor info, both must be changed.
- **Date/time** auto-populate on load; `clearForm()` resets them to now but preserves the doctor name and specialty fields.

## Testing

No test suite. Verify changes by opening `recetario.html` in a browser (no server required), filling in fields, and clicking "Descargar receta PDF" to inspect the generated PDF output.
