

Demo: https://claude.ai/public/artifacts/0b0a18df-92a6-4abd-86fd-15892b221167

# 📚 Listo (pending name) — List Books in Seconds

A peer-to-peer marketplace for Russian children's books. Parents photograph books, create listings, and share them with buyers through Facebook Groups and beyond.

**The problem:** Selling 100 outgrown kids' books takes an entire day — photographing each one, researching prices, typing descriptions in Cyrillic, posting to multiple groups, then drowning in "is this available?" messages.

**Listo cuts that to minutes.** Create a shelf, add books, share one link. Buyers browse, reserve, and pay — all tracked in one place.

---

## ✨ Features

**For Sellers**
- Create bookshelves with bundle deals (take-all pricing, pick-X deals)
- Add books with title, author, price, condition, age range, series
- Set hold timers (6h / 12h / 24h / 48h) for reservations
- Share a single link to Facebook Groups, WhatsApp, Telegram
- Track payments — buyers confirm they sent, sellers confirm they received
- Mark books as sold, sold elsewhere, or available

**For Buyers**
- Browse public bookshelves without logging in
- See bundle deals and series groupings
- Select books and reserve with one tap
- Pay outside the app (Zelle, Venmo) — no fees
- Confirm payment sent

**Payment Flow**
> Buyer reserves → App shows seller's Zelle/Venmo → Buyer pays outside → Buyer taps "I sent payment" → Seller taps "Payment received" → Done

No payment processing, no Stripe fees, no PCI compliance. The app just tracks the handshake.

---

## 🛠 Tech Stack

- **Frontend:** React 18 + Vite
- **Styling:** Tailwind CSS (warm bookish palette — cream, terracotta, sage)
- **Backend:** Supabase (PostgreSQL, Auth, Storage, Row Level Security)
- **Auth:** Google OAuth
- **Hosting:** Vercel
- **Icons:** Lucide React

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- A [Supabase](https://supabase.com) project (free tier works)
- A [Vercel](https://vercel.com) account (free tier works)

### Local Development

```bash
# Clone the repo
git clone https://github.com/YOUR-USERNAME/listo-app.git
cd listo-app

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Edit .env.local with your Supabase credentials

# Run the database schema
# Copy supabase-schema.sql contents into Supabase SQL Editor and run

# Start dev server
npm run dev
```

### Environment Variables

| Variable | Description |
|----------|-------------|
| `VITE_SUPABASE_URL` | Your Supabase project URL |
| `VITE_SUPABASE_ANON_KEY` | Your Supabase anonymous (public) key |

### Demo Mode

The app works without Supabase credentials — it loads mock data with real Russian children's book titles (Астрид Линдгрен, Тося-Бося series, Чик и Брики, and more). Useful for previewing the UI.

---

## 📁 Project Structure

```
listo-app/
├── src/
│   ├── App.jsx          # Complete app — all screens and logic
│   ├── supabase.js      # Supabase client + demo mode fallback
│   ├── main.jsx         # React entry point
│   └── index.css        # Tailwind imports
├── supabase-schema.sql  # Database schema — run in Supabase SQL Editor
├── DEPLOY-GUIDE.md      # Step-by-step deployment (no dev experience needed)
├── index.html
├── package.json
├── tailwind.config.js
├── vite.config.js
└── vercel.json
```

---

## 🗃 Database Schema

| Table | Purpose |
|-------|---------|
| `profiles` | User profiles (auto-created on signup), payment methods |
| `bookshelves` | Collections of books for sale — bundles, hold timer, shipping settings |
| `books` | Individual books — title, author, price, condition, status, series |
| `orders` | Reservations and payment tracking lifecycle |
| `order_items` | Books within each order |

Full schema with Row Level Security, indexes, and auto-profile creation trigger in `supabase-schema.sql`.

---

## 📱 Screens

| Screen | Description |
|--------|-------------|
| Login | Google OAuth, demo mode indicator |
| My Library | Shelves overview, stats (available / on hold / earned) |
| Shelf Detail | Books list with status filters, share button, add book FAB |
| Add/Edit Book | Form with title, author, price, condition, series, age range |
| Create Shelf | Name, hold timer, take-all deal toggle |
| Activity | Orders with status badges, payment confirmation actions |
| Buyer View | Public bookshelf — select books, see bundles, reserve |
| Profile | Payment methods, sign out |

---

## 🎯 Target Audience

Russian-speaking families in the US (starting with Seattle area) who want to:
- **Sell** outgrown children's books to other families
- **Buy** affordable Russian-language books for their kids
- **Maintain** bilingual reading habits despite import challenges

---

## 🗺 Roadmap

- [x] Core seller flow (shelves, books, pricing)
- [x] Buyer reservation and payment tracking
- [x] Bundle deals (take-all, pick-X)
- [x] Shareable public links
- [ ] Photo upload for book covers
- [ ] AI batch scanning (photo of 10 books → auto-detect all titles)
- [ ] Search and browse across all sellers
- [ ] Push notifications
- [ ] In-app messaging
- [ ] Custom domain

---





---

Built with ☕ and outgrown books by a parent who spent an entire day listing 100 books manually and decided: never again.

