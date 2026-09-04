# Greenhouse order management website

Open `index.html` in a modern browser. This prototype keeps its data in the browser's local storage so staff can test the full workflow without a server.

## What it does

- Maintains orders for Sobeys, Food Basics, Foodland, FreshCo, and Canadian Tire at the individual-store level.
- Maintains a store delivery list with store number, address, multiple contact names, and contact details.
- Maintains a SKU product catalogue that fills product, variety, and pot-size information during order entry.
- Provides an editable Store Ads & Specials planning sheet with grower/ad weeks, item and SKU details, pricing, margin, quantities, notes, and automatically calculated cost.
- Creates a new order directly from a selected ad row and destination store, converting ordered units into full carts and remaining pots.
- Captures carts and partial-cart pots separately.
- Provides a production-facing Greenhouse view that automatically excludes cancelled order lines.
- Tracks cancellations with date, responsible person, and notes.
- Displays active orders, cancellations, upcoming deliveries, and customer totals.
- Uses status and pot-size dropdowns, validation for required fields, and an in-app cancellation alert.

## Production Microsoft 365 deployment

Use a SharePoint List or Dataverse as the shared order database, host the site in Azure Static Web Apps or as a SharePoint Framework application, and authenticate with Microsoft Entra ID. Replace the browser storage functions in `app.js` with Microsoft Graph or Dataverse calls.

Create a Power Automate flow that starts when the database row changes. When Status is `Cancelled`, send an email to the greenhouse distribution list and post to the greenhouse Teams channel. Include Customer, Store Number, delivery address, Order Number, SKU, Product, Variety, Pot Size, Carts, Partial-cart Pots, Delivery/Pickup Date, Changed By, and Notes. Use a cancellation-alert flag or a flow condition that detects a change to the status to prevent repeat messages.

