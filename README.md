# 🛍️ BeltRo - Bulk Children Belts Maker & Distributor

<div align="center">

![Next.js](https://img.shields.io/badge/Next.js-15.1-black?style=for-the-badge&logo=next.js)
![React](https://img.shields.io/badge/React-19-blue?style=for-the-badge&logo=react)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.4-38B2AC?style=for-the-badge&logo=tailwind-css)
![Clerk](https://img.shields.io/badge/Clerk-Auth-6C47FF?style=for-the-badge&logo=clerk)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?style=for-the-badge&logo=mongodb)

**"Belts with best quality and price"**  
*India's leading bulk school uniform and custom crest belts manufacturer based in Byculla, Mumbai since 2017.*

</div>

---

## 📖 Overview

**BeltRo** is a full-stack, enterprise-grade e-commerce application designed for India's premier maker and bulk distributor of children's school belts, customized crest buckles, student stretch belts, and formal belts. 

Engineered with **Next.js 15 App Router** and **React 19**, it couples a high-converting, accessible **Buyer Experience** with an administrative **Seller CMS & Fulfillment Suite**.

---

## 🎨 Design System: 06 Deep Blue Palette

The visual identity is built around the **06 Deep Blue** theme (Professional • Strong • Reliable):

| Role | Color Name | Hex Code | Purpose |
| :--- | :--- | :--- | :--- |
| **Darkest** | Navy Slate | `#0B1220` | Primary headers, footer, high-contrast text |
| **Navy Accent** | Academic Deep Blue | `#1E3A8A` | Trust banners, hero gradients, dark cards |
| **Primary** | Vibrant Royal Blue | `#2563EB` | Interactive buttons, active tabs, links, badges |
| **Light Tint** | Soft Ice Blue | `#93C5FD` | Borders, subtle highlights, pill chips |
| **Background** | Clean Ice Background | `#EFF6FF` | Card backgrounds, hover states, input fills |

---

## ⚡ Core Tech Stack

- **Framework**: Next.js 15+ (App Router, Turbopack, Server Actions & REST API Route Handlers)
- **UI Library**: React 19
- **Styling**: Tailwind CSS 3.4+ with custom glassmorphism, responsive drawers, and image drag protection
- **Authentication**: Clerk Authentication (`@clerk/nextjs`) with multi-role permissions (`buyer`, `junior_seller`, `seller`)
- **Database**: MongoDB with Mongoose 8+ ODM (Connection pooling and global schema caching)
- **Asset Storage**: Cloudinary for multi-image uploads and product assets
- **Background Jobs**: Inngest for event-driven serverless workflows (Clerk webhook synchronization & order notifications)
- **HTTP Client**: Axios with Bearer token authentication
- **Notifications**: React Hot Toast
- **Icons**: Lucide React / Custom SVG Component Icons
- **Effects**: Canvas Confetti

---

## 🌟 Comprehensive Feature Suite

### 🛒 1. Buyer Experience & Storefront

- **Interactive Lightbox & Cursor Zoom**:
  - High-resolution main image with cursor-following **2.5x magnification zoom**.
  - Click-to-expand fullscreen lightbox with pan, scale, and mobile pinch-to-zoom.
  - **Keyboard Navigation**: Left & Right arrow keys navigate through thumbnail gallery.
- **Dynamic Color Engine (`lib/colorEngine.js`)**:
  - Direct swatches for standard solid shades (*Black, Navy, Silver, Gold, etc.*).
  - Dual-tone diagonal gradient split swatches for composite colors (e.g., *"Navy & Silver"*, *"Blue & Black"*).
  - Deterministic vibrant HSL color hashing for custom color names.
- **Multi-Filter Product Catalog (`/all-products`)**:
  - Dual-column responsive layout (desktop sidebar, mobile slide drawer).
  - Multi-checkbox filters: Categories (*school belts*, *Casual belts*, *Customised belts*, *Regular belts*) and Brands.
  - Interactive price range slider and **In-Stock Only** availability toggle.
  - Live search bar matching product title, description, and SKU model codes.
  - Sorting options: *Featured / Best Sellers*, *Price: Low to High*, *Price: High to Low*, *Newest Arrivals*.
- **Interactive Lightbox & Stock Engine**:
  - Original price strikethrough, highlighted offer price, and percentage savings chip.
  - Live stock status badges: *"In Stock"* (green), *"Only X Left"* (amber pulse), or *"Out of Stock"* (red with disabled Add to Cart).
  - Dynamic product specifications table mapped with Lucide icons via `lib/specIcons.js`.
- **Full-Featured Review & Rating Subsystem**:
  - Aggregate rating summary card with star average and visual distribution progress bars (5, 4, 3, 2, 1 stars).
  - *"Write a Review"* modal with interactive 5-star selector, title, and body.
  - Verified buyer badges, helpful upvote toggle, offensive report flags, and threaded nested replies.
- **Cart & Order Summary Sidebar**:
  - Item listing with quantity steppers (`+` / `-`), color indicator swatches, and model SKU codes.
  - Live promo coupon validation engine with instant percentage deductions.
  - Automatic shipping fee calculation with free shipping threshold progress tracker.
- **Address Selection & Checkout (`/add-address`)**:
  - Multi-address manager with full name, phone number, pin code, area, city, and state.
  - Payment method selector: Cash on Delivery (COD) or Online UPI/Card.
- **Order Placed Celebration (`/order-placed`)**:
  - Full-screen celebration confetti animation.
  - Order reference number and dispatch milestone details.
- **Visual Order Status Tracker (`/my-orders`)**:
  - 4-milestone visual status bar: `Order Placed` ➔ `Processing` ➔ `Shipped` ➔ `Delivered`.
  - Compulsory **Rejection Explanation Notice**: Clearly highlights the seller's specific `rejectReason` if an order is cancelled or rejected.
- **Saved Wishlist Gallery (`/wishlist`)**:
  - Heart toggle on all cards with instant synchronization and single-click Add to Cart.
- **Profile Management (`/user-profile`)**:
  - Customer contact details, phone number, and Clerk metadata role viewer.
- **Native Experience & Image Protection**:
  - Globally disabled browser image dragging (`select-none pointer-events-none`) for a native app feel.

---

### 🏬 2. Seller Dashboard CMS & Admin Suite (`/seller`)

- **RoleGuard Protection**:
  - Strict client-side and API permission barrier separating `junior_seller` (inventory & order fulfillment only) from full `seller` / `admin` (pricing, CMS, promotions, settings).
- **Add Product Suite (`/seller`)**:
  - Upload up to 4 product images with drag-and-drop preview and Cloudinary integration.
  - Product Name, Category dropdown, Brand selector, unique SKU model code.
  - Price and Offer Price fields with real-time automatic margin calculation.
  - Color Picker supporting standard colors, dual-tone names, and hex codes.
  - Dynamic Specification Builder: Add dynamic key-value pairs (e.g., *"Material": "Die-cast Brass"*, *"Width": "30 mm"*).
  - Rich Text Toolbar: Bold, Italics, Lists, Code, Blockquotes, and side-by-side Markdown preview.
- **Edit Product Page (`/seller/edit/[id]`)**:
  - Full product modification suite for existing catalog items.
- **Inventory Management Table (`/seller/product-list`)**:
  - Searchable, sortable data table showing product thumbnail, name, SKU, category, price, stock count, and safe delete modals.
- **Order Fulfillment Center (`/seller/orders`)**:
  - Comprehensive customer orders list with delivery address, phone, item quantities, and payment status.
  - Direct status dropdown: change status to `Processing`, `Shipped`, or `Delivered`.
  - **Mandatory Rejection Modal**: Prompts the seller for a compulsory `rejectReason` before rejecting any order.
- **Printable Tax Invoices (`/seller/invoice/[id]`)**:
  - Itemized customer invoices with GSTIN data, tax breakdown, and customer delivery address.
  - Tailored CSS media print styles for both standard **A4** and **Thermal** receipt printers.
- **Sales Analytics Dashboard (`/seller/analytics`)**:
  - Gross sales metrics, total orders, average basket size, and low-stock alerts table (&le; 5 units).
- **Promo Coupon Engine (`/seller/promo`)**:
  - Discount code generator with percentage rates, max usage caps, and product scoping (`all`, `specific`, `exclude`).
  - Integrated `CalendarPicker` for custom expiration dates.
- **Review Moderation Desk (`/seller/reported-reviews`)**:
  - Flagged reviews and replies moderation with one-click removal actions.
- **Dynamic Content Management System (CMS)**:
  - **Hero Slider Manager (`/seller/slider`)**: Upload slides, headline copy, subheadings, discount chips, and CTA links.
  - **Featured & Popular Pickers (`/seller/featured`, `/seller/popular`)**: Checkbox pickers to highlight specific belts on the storefront.
  - **Promotional Banner Customizer (`/seller/banner`)**: Mid-page discount banner customizer.
  - **Brand & Logo Configuration (`/seller/logo`)**: Site emblem, motto tagline, and established year.
  - **Theme Accent Color Switcher (`/seller/theme`)**: Switch between Deep Blue, Classic Navy, or custom hex overrides.
  - **Global Store Settings (`/seller/settings`)**: Currency symbol, factory address, contact helpline, free shipping threshold.
  - **Markdown CMS Editors (`/seller/about`, `/seller/contact`)**: Real-time side-by-side markdown editors for About Us and Contact pages.

---

## 🗄️ Database Architecture & Schemas

The application is backed by 7 Mongoose schemas:

1. **User (`models/User.js`)**: Synced with Clerk authentication; stores cart dictionary and wishlist IDs.
2. **Product (`models/Product.js`)**: SKU model code, category, color, stock, images array, and dynamic specifications.
3. **Order (`models/Order.js`)**: Item references, delivery address, amounts, payment method/status, and compulsory rejection reason.
4. **PromoCode (`models/PromoCode.js`)**: Coupon codes, discount percentages, usage counters, expiration dates, and product scopes.
5. **Review (`models/Review.js`)**: 1-5 star ratings, photo attachments, helpful upvotes, report flags, and nested replies.
6. **Address (`models/Address.js`)**: Saved shipping addresses per user.
7. **SiteSettings (`models/SiteSettings.js`)**: Key-value NoSQL CMS store for real-time site customization.

---

## 📁 Project Directory Tree

```
BeltRo/
├── app/
│   ├── layout.js                     # Root layout with ClerkProvider & AppContextProvider
│   ├── page.jsx                      # Storefront home page (Hero, Featured, Banners, Products)
│   ├── globals.css                   # Custom utilities, image drag protection, color engine CSS
│   ├── all-products/page.jsx         # Product catalog with multi-filters, brand selection & search
│   ├── product/[id]/page.jsx         # Product details with lightbox, specs, stock & review system
│   ├── cart/page.jsx                 # Shopping cart, promo code application & price breakdown
│   ├── add-address/page.jsx          # Shipping address form and selector
│   ├── my-orders/page.jsx            # Buyer order history and status tracker
│   ├── order-placed/page.jsx         # Order confirmation with confetti & receipt preview
│   ├── wishlist/page.jsx             # Saved items gallery with instant Add to Cart
│   ├── user-profile/page.jsx         # Custom profile management (username, phone, avatar)
│   ├── about/page.jsx                # Dynamic Markdown About Us page loaded from CMS
│   ├── contact/page.jsx              # Dynamic Contact page loaded from CMS
│   ├── privacy-policy/page.jsx       # Dynamic Privacy Policy loaded from CMS
│   ├── seller/
│   │   ├── layout.jsx                # Seller layout with responsive sidebar & role check
│   │   ├── page.jsx                  # Add Product page with Cloudinary upload & specifications
│   │   ├── edit/[id]/page.jsx        # Edit existing product
│   │   ├── product-list/page.jsx     # Product inventory management with live search & toggles
│   │   ├── orders/page.jsx           # Order fulfillment center with rejection handling
│   │   ├── invoice/[id]/page.jsx     # Printable thermal & A4 customer invoice
│   │   ├── analytics/page.jsx        # Sales analytics, top sellers & revenue graphs
│   │   ├── promo/page.jsx            # Discount code generator (limits, expiry, scopes)
│   │   ├── reported-reviews/page.jsx # Moderation desk for flagged reviews & replies
│   │   ├── slider/page.jsx           # Hero carousel CMS manager
│   │   ├── featured/page.jsx         # Featured products picker CMS
│   │   ├── popular/page.jsx          # Popular trending products picker CMS
│   │   ├── banner/page.jsx           # Mid-page promo banner CMS
│   │   ├── logo/page.jsx             # Site logo configuration
│   │   ├── theme/page.jsx            # Dynamic theme accent color switcher
│   │   ├── settings/page.jsx         # Global store settings CMS
│   │   ├── about/page.jsx            # Rich Markdown editor for About Us
│   │   └── contact/page.jsx          # Rich Markdown editor for Contact Info
│   └── api/                          # REST API route handlers (28 endpoints)
├── components/                       # Storefront & seller components
├── config/                           # Database & Inngest client configurations
├── context/                          # Global AppContext state provider
├── models/                           # Mongoose schemas (User, Product, Order, PromoCode, etc.)
└── lib/                              # Spec icon mapper & color engine
```

---

## 🏭 Factory & Institutional Wholesale

**BeltRo Manufacturing Unit**  
Byculla East, Mumbai, Maharashtra 400027, India  
- **Wholesale Contact**: +91 98200-BELTRO  
- **Institutional Inquiries**: wholesale@beltro.in  
- **Established**: 2017  

---

## 📄 License

This project is proprietary and built for **BeltRo**. All rights reserved.
