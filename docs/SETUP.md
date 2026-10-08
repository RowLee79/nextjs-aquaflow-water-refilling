# AquaFlow — Water Refilling Management System

A Next.js and Cloudflare D1 app for customer records, water products, refilling and delivery orders, stock, returnable containers, payment records, balances, and CSV export. Prices use Philippine pesos and are stored as integer centavos.

## Requirements and setup

1. Install Node.js 22.13 or newer.
2. Extract the ZIP and enter the `aquaflow-refilling` folder.
3. Run `npm ci`.
4. Run `npm run dev` and open the displayed local address.
5. In **Products**, choose **Load sample products**. This inserts five sample products into an empty catalog. Add a customer, then create an order.

The D1 database binding is named `DB` in `.openai/hosting.json`. The included initial migration is `drizzle/0000_wise_madrox.sql`. The starter's local Workers runtime handles the database in development. If changing `db/schema.ts`, run `npm run db:generate` and apply the new migration. For a separate Cloudflare deployment, configure an equivalent D1 binding, apply migrations, and adapt the Sites-specific build scripts.

## Supported flows

- Manage customers with phone and delivery address; add water products, unit pricing, stock and active state.
- Create pickup or delivery orders. The order stores item quantity, fulfillment address, optional driver, container counts, and an initial payment. Creating an order deducts product stock.
- Move orders through Queued → Processing → Ready → Completed (pickup), or through Out for delivery before Completed (delivery). Cancelling an active order restores stock; it does not issue a refund.
- Record later payments up to the unpaid balance. Record returned containers against a specific order, within the number issued on that order.
- See a dashboard, customer container balances, payment history, order search and CSV export.

## Validation

`npx tsc --noEmit` checks TypeScript. `npm run build` builds the Workers-compatible app.

## Before public or production use

This is an operational demo. Add staff authentication, role permissions, audit logs, backup procedures and abuse controls. Payment entries are manual records, with no live payment processing or automatic refunds. Expand stock accounting for concurrent high-volume operations, container deposits and cross-order returns, route planning, receipts, supplier procurement, and sanitation/quality-control records according to your business rules.
