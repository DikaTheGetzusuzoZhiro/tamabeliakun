# TAMA Store — Pink / White / Black

Static Vercel-ready storefront using Supabase.

## Fitur
- Public catalog with search
- Budget filters: 20–100rb and 200–1jt
- Admin `/admin` with Supabase Auth
- Add/edit/delete products
- 1 thumbnail + multiple specification images
- Price validation against selected budget
- Pink / white / black UI with dark mode
- Username-only customer login
- Live chat by username + category, with admin replies and close chat
- Ratings/reviews with username field, stars, and text
- Hamburger menu with Community, TikTok, and WhatsApp links
- Product details include a “Lanjutkan via WhatsApp” button
- Supabase RLS + exact-parameter RPC for chat

## Setup
1. Create a Supabase project.
2. In Authentication → Users, create `fyesty8@gmail.com` and set its password there.
3. Open SQL Editor and run **all** of `supabase.sql` (the SQL now accepts the fixed admin email even when the `admins` row was not inserted earlier).
4. If the Live Chat previously showed `get_or_create_chat ... schema cache`, run the SQL again; the script drops/recreates the RPC with the exact parameters `p_category, p_token, p_username` and sends a PostgREST schema reload.
5. Open `config.js` and replace:
   - `YOUR_PROJECT` in the Supabase URL
   - `YOUR_SUPABASE_ANON_KEY` with the project's public anon key.
5. Push the whole folder to GitHub and import the repo into Vercel.
6. Public site is `/`, admin panel is `/admin`.

## Important
- Do NOT put a `service_role` key in `config.js`.
- Do NOT hard-code the admin password in frontend code. Supabase Auth handles it.
- The blue banner supplied by the user is stored as `assets/banner.png`.
