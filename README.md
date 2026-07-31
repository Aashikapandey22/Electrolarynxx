# GrapheneLabs — Smart Electrolarynx

A high-end, scroll-driven e-commerce experience for the **GrapheneLabs Smart Electrolarynx** — a next-generation assistive device that gives voice back to users. Built with React, Three.js (React Three Fiber), Framer Motion, and the Base44 BaaS platform.

> Price: ₹20,000 · Free shipping · 1-year warranty · 30-day returns

---

## ✨ Features

- **Cinematic 3D product viewer** — an interactive, explodable model of the electrolarynx rendered with React Three Fiber, with scroll-triggered camera choreography, cross-section reveals, and interactive component hotspots.
- **Scroll-driven storytelling** — a multi-section landing page that animates content into view as you scroll, powered by Framer Motion.
- **Color customization** — four premium anodized finishes (Arctic White, Graphite Black, Titanium Silver, Medical Blue) with live 3D material updates.
- **Full checkout flow** — shipping + payment form, order persistence via the Base44 `Order` entity, and an animated order confirmation page.
- **Authentication** — email/password + Google OAuth, OTP verification, and password reset, all wired through Base44 Auth.
- **Responsive** — designed mobile-first and fully responsive across devices.

---

## 🧱 Tech Stack

| Layer | Technology |
|------|-----------|
| Framework | React 18 + Vite |
| Styling | Tailwind CSS + shadcn/ui (Radix) |
| 3D / Animation | Three.js, @react-three/fiber, @react-three/drei, Framer Motion, GSAP |
| Routing | React Router v6 |
| Data / Auth / Backend | Base44 SDK (`@base44/sdk`) |
| Forms | React Hook Form + Zod |
| State / Data fetching | TanStack React Query |

---

## 📂 Project Structure

```
src/
├─ pages/
│  ├─ VoxaLife.jsx            # Landing page (scroll-driven 3D experience)
│  ├─ Product.jsx             # Product detail + buy page
│  ├─ Checkout.jsx            # Shipping + payment checkout
│  ├─ OrderConfirmation.jsx    # Order success / details
│  ├─ Login.jsx / Register.jsx / ForgotPassword.jsx / ResetPassword.jsx
├─ components/
│  ├─ voxalife/
│  │  ├─ SceneCanvas.jsx       # 3D scene: camera rig, lighting, hotspots
│  │  ├─ ElectrolarynxModel.jsx # The 3D device model (explodable)
│  │  ├─ ProductViewer.jsx     # Static 3D viewer for the product page
│  │  ├─ StoryContent.jsx      # Scrollable landing-page sections
│  │  ├─ Navigation.jsx        # Top nav bar
│  │  ├─ ColorSwitcher.jsx      # Color variant selector
│  │  ├─ SpecsSection.jsx       # Animated specs counters
│  │  ├─ HotspotCard.jsx        # Interactive hotspot info card
│  │  ├─ VocalWaveform.jsx      # Voice waveform overlay
│  │  ├─ Loader.jsx             # Startup loading animation
│  │  └─ sceneUtils.js          # Camera keyframes, color variants, hotspot data
│  └─ ui/                      # shadcn/ui primitives
├─ App.jsx                    # Router + auth providers
└─ index.css                  # Design tokens (Tailwind theme)

base44/
└─ entities/
   └─ Order.jsonc             # Order entity schema
```

---

## 🗂️ Data Model

### `Order`
Stores a completed purchase.

| Field | Type | Notes |
|------|------|------|
| `order_number` | string | e.g. `GL-...` |
| `product_name` | string | "GrapheneLabs Smart Electrolarynx" |
| `color_variant` | string | Selected finish name |
| `quantity` | integer | default 1 |
| `unit_price` | number | ₹20,000 |
| `total_price` | number | subtotal + tax |
| `customer_name` | string | |
| `customer_email` | string | |
| `shipping_address` | string | |
| `city` / `postal_code` / `country` | string | |
| `card_last4` | string | last 4 digits of card |
| `status` | enum | `confirmed` · `shipped` · `delivered` · `cancelled` |

---

## 🚀 Getting Started

### Prerequisites
1. Clone the repository.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Install the Base44 CLI (optional, for full-stack dev):
   ```bash
   npm install -g base44@latest
   ```

### Run Locally (full stack)
```bash
base44 dev
```
This starts the local Base44 backend and the Vite frontend together.

### Run Frontend Only
```bash
npm run dev
```
Open the local URL printed by Vite. For frontend-only work against the hosted backend, create a `.env.local`:

```bash
VITE_BASE44_APP_ID=your_app_id
VITE_BASE44_APP_BASE_URL=https://your-app.base44.app
```

---

## 🛠️ Available Scripts

| Script | Description |
|-------|------------|
| `npm run dev` | Start the Vite dev server |
| `npm run build` | Production build |
| `npm run preview` | Preview the production build |
| `npm run lint` | Lint with ESLint |
| `npm run lint:fix` | Auto-fix lint issues |
| `npm run typecheck` | Type-check with TypeScript |

---

## 🎨 Customization

- **Color variants & 3D materials** — edit `COLOR_VARIANTS` in `src/components/voxalife/sceneUtils.js`.
- **Camera choreography** — adjust `CAMERA_KEYFRAMES` in the same file.
- **Component hotspots** — edit `HOTSPOT_DATA` in `sceneUtils.js`.
- **Product price** — `PRICE` constant in `src/pages/Product.jsx` and `src/pages/Checkout.jsx`.
- **Design tokens** — colors, fonts, radius in `src/index.css` (mapped via `tailwind.config.js`).

---

## 📦 Publishing

After pushing changes to git, open the Base44 dashboard and publish:

```bash
base44 dashboard open
```

---

## 📚 Docs & Support

- Base44 Docs: [https://docs.base44.com](https://docs.base44.com)
- Base44 CLI reference: [https://docs.base44.com/developers/references/cli/commands/introduction](https://docs.base44.com/developers/references/cli/commands/introduction)
- Support: [https://app.base44.com/support](https://app.base44.com/support)

---

© 2026 GrapheneLabs. All rights reserved.
