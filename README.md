# Forever Frontend - Customer Store

React-based customer-facing storefront for the Forever e-commerce application.

## Tech Stack

- React 18
- Vite
- Tailwind CSS
- React Router v6
- Axios
- React Toastify

## Project Structure

```
src/
├── main.jsx                    # Entry point with Router & Context
├── App.jsx                     # Route definitions & layout
├── index.css                   # Tailwind + Google Fonts
├── assets/
│   └── assets.js               # Asset references
├── components/
│   ├── BestSeller.jsx          # Best seller products section
│   ├── CartTotal.jsx           # Cart total summary
│   ├── Footer.jsx              # Site footer
│   ├── Hero.jsx                # Homepage hero banner
│   ├── LatestCollection.jsx    # Latest products section
│   ├── Navbar.jsx              # Navigation bar with cart/profile
│   ├── NewsletterBox.jsx       # Email subscription box
│   ├── OurPolicy.jsx           # Exchange/Return/Support policies
│   ├── ProductItem.jsx         # Product card component
│   ├── RelatedProducts.jsx     # Related products on product page
│   ├── SearchBar.jsx           # Search bar (collection page)
│   └── Title.jsx               # Section title component
├── context/
│   └── ShopContext.jsx         # Global state (products, cart, auth)
└── pages/
    ├── About.jsx               # About us page
    ├── Cart.jsx                # Shopping cart page
    ├── Collection.jsx          # Product listing with filters
    ├── Contact.jsx             # Contact information page
    ├── Home.jsx                # Homepage
    ├── Login.jsx               # Login / Sign up page
    ├── Orders.jsx              # User order history
    ├── PlaceOrder.jsx          # Checkout page (address + payment)
    ├── Product.jsx             # Single product detail page
    └── Verify.jsx              # Stripe payment verification
```

## Features

- **Product Browsing** — Grid layout with hover effects
- **Filtering** — By category (Men, Women, Kids) and type (Topwear, Bottomwear, Winterwear)
- **Sorting** — Price low-to-high, high-to-low, relevant
- **Search** — Real-time product search on collection page
- **Product Detail** — Multiple images, size selection, star ratings, related products
- **Shopping Cart** — Add/remove items, quantity updates, size display
- **Authentication** — Login & registration with JWT
- **Checkout** — Delivery form, COD or Stripe payment
- **Order Tracking** — View order status and history
- **Responsive** — Mobile-first design with Tailwind CSS

## Prerequisites

- Node.js 18+
- npm
- Backend running on http://localhost:4000

## Setup

### Install Dependencies

```bash
npm install
```

### Configure Environment

Create a `.env` file in the project root:

```
VITE_BACKEND_URL=http://localhost:4000
```

### Run Development Server

```bash
npm run dev
```

Opens at http://localhost:5173

### Build for Production

```bash
npm run build
```

Output in `dist/` folder.

### Preview Production Build

```bash
npm run preview
```

## Pages

| Route | Page | Description |
|-------|------|-------------|
| `/` | Home | Hero, latest collections, best sellers, policies |
| `/collection` | Collection | All products with filters & sorting |
| `/product/:id` | Product | Product detail with images & sizes |
| `/cart` | Cart | Shopping cart with totals |
| `/login` | Login | Login / Sign up form |
| `/place-order` | Place Order | Delivery info + payment method |
| `/orders` | Orders | User order history & tracking |
| `/about` | About | About us page |
| `/contact` | Contact | Store info & careers |
| `/verify` | Verify | Stripe payment callback |

## State Management

Uses React Context (`ShopContext`) for global state:

- `products` — All products from API
- `cartItems` — Cart state (nested object: `{ productId: { size: quantity } }`)
- `token` — JWT auth token (persisted in localStorage)
- `search` / `showSearch` — Search state
- Helper functions: `addToCart`, `updateQuantity`, `getCartCount`, `getCartAmount`

## API Integration

All API calls go through Axios to the backend URL configured in `.env`:

- Auth token sent via `token` header
- Products fetched on app load
- Cart synced with backend when user is logged in
- Orders placed via `/api/order/place` (COD) or `/api/order/stripe` (card)
