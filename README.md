# AquaFlow — Water Refilling Management System

A Next.js and Cloudflare D1 app for customer records, water products, refilling and delivery orders, stock, returnable containers, payment records, balances, and CSV export. Prices use Philippine pesos and are stored as integer centavos.

Portfolio demonstration by RowLee Tanawan. The implementation uses Next.js-compatible App Router APIs with the Vinext runtime; deployment targets Cloudflare Workers. It is not a conventional standalone `next dev` deployment.

## Features

- Manage customers with phone and delivery address; add water products, unit pricing, stock and active state.
- Create pickup or delivery orders. The order stores item quantity, fulfillment address, optional driver, container counts, and an initial payment. Creating an order deducts product stock.
- Move orders through Queued → Processing → Ready → Completed (pickup), or through Out for delivery before Completed (delivery). Cancelling an active order restores stock; it does not issue a refund.
- Record later payments up to the unpaid balance. Record returned containers against a specific order, within the number issued on that order.
- See a dashboard, customer container balances, payment history, order search and CSV export.

## Technology

React, TypeScript, Next.js-compatible App Router, Vinext, Vite and responsive CSS. Cloudflare D1 SQLite and Drizzle migrations provide persistent data.

## Run locally

Node.js 22.13+ is required. Follow [installation, database initialization and walkthrough instructions](docs/SETUP.md), including the project-specific migration command. Dependencies and local database files are excluded from source control.

## Screenshots

Actual application screenshots are pending capture. No mockup is presented as a running application screenshot.

## Project layout

- `app/page.tsx`: application interface
- `app/globals.css`: responsive styling
- `app/api/`: server workflows, where applicable
- `db/` and `drizzle/`: schema and migrations, where applicable
- `docs/SETUP.md`: full setup, workflow rules and limitations

## Demo scope

Use fictional data for portfolio demonstrations. See [documented limitations](docs/SETUP.md) before deployment; authentication, payment integrations and operational safeguards vary by project and are not implied by the portfolio presentation.
