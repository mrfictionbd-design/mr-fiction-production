# MR. FICTION — Production Storefront

Public-facing dark editorial streetwear storefront for Bangladesh.

## Production stack
- Static HTML storefront deployed through Vercel
- Supabase Postgres catalogue and order records
- Supabase Edge Function `checkout` for guest Cash on Delivery orders
- GitHub `main` → Vercel production deployments

## Storefront behavior
- Live catalogue reads active products from Supabase
- Size selection (S–XXL) and persistent local cart
- Guest COD checkout with name, Bangladesh mobile number, delivery address and city
- Server-side product price lookup (client prices are never trusted)
- Delivery charge: ৳80 for Dhaka, ৳130 outside Dhaka
- Checkout idempotency and per-IP request throttling
- Order, order items and order event are stored in Supabase

## Deploy
The Vercel project is `mr-fiction-production`. The assigned project domain is:
https://mr-fiction-production.vercel.app/

Pushes to `main` create production deployments.

## Launch limitations — do not start paid ads until these are resolved
1. Replace the current editorial/stock placeholder product imagery with the actual MR. FICTION product photos and verify each SKU, size and stock quantity. The private `MR.-FICTION-PRODUCT-ZIP` repository is currently empty.
2. Confirm live prices, size availability, and delivery fee policy with the business.
3. Add the real Meta Pixel ID and verify PageView, ViewContent, AddToCart, InitiateCheckout and Purchase events in Meta Events Manager. No Pixel ID was available during this build.
4. Confirm a customer-care WhatsApp number and publish accurate shipping, exchange/return and privacy policies.
5. Complete a real owner-supervised COD test order and confirm the admin/dashboard can view and update it.
6. Configure and test a Bangladesh online payment provider only if online payments are required. COD is the only enabled payment method.

## Security notes
- Browser uses only the Supabase publishable key.
- Checkout validates product status, server-side prices, phone/address fields, quantity and size.
- Supabase service-role credentials remain in Edge Function secrets and are never embedded in the storefront.
- Do not expose database service credentials in GitHub or browser code.
