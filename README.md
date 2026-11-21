# VIN Decoder

A static, single-page VIN (Vehicle Identification Number) decoder to split the code into its ISO 3779 segments, look up the model year and manufacturer, and verify the check digit.

Everything runs in the browser. Nothing is shared with a server.

## Features

- Validates VIN format (17 characters; digits and letters except `I`, `O`, `Q`)
- Breaks the VIN into WMI, VDS, check digit, model year, plant, and VIS segments
- Partial WMI lookup for common manufacturers, plus Fiat VDS model codes
- Model-year lookup (nearest year cycle)
- ISO 3779 / FIPS 115-1 check-digit calculation with a step-by-step arithmetic table
- Shareable results via the `?vin=` query parameter
- Spanish UI when the browser's default language is Spanish; English otherwise
- Keyboard-accessible, responsive dark UI with screen-reader announcements

## Usage

Open `index.html` directly in a modern browser, or visit the deployed GitHub Pages site. Enter/Paste a VIN and select **Decode VIN**, or use one of the example chips.

Decoded VINs are stored in the URL as `?vin=…`, so you can bookmark or share them.

## Development

There is no build step, package manager, or external dependency. Edit `index.html` and reload the page.

## Deployment

Pushes to `main` trigger [`.github/workflows/deploy-pages.yml`](.github/workflows/deploy-pages.yml), which uploads the repository root as a GitHub Pages artifact and deploys it via the official Pages actions.

One-time setup in the repository settings: **Pages → Build and deployment → Source: GitHub Actions**.

## Limitations

WMI and model-year codes are standardized, but the VDS, plant code, and serial number are manufacturer-defined. The built-in lookup covers only a subset of WMIs and Fiat models, and the model year picks the closest cycle to the current year — a full build-sheet decode requires the manufacturer's own database. Some decodes may be incomplete or informational only.
