# Paradise Nursery Shopping Cart Application

A single-page React shopping application for **Paradise Nursery**, an online house-plant
store. Users browse a catalogue of house plants grouped by category, add them to a
shopping cart, and adjust or remove the items in the cart before checkout.

Final project for the IBM *Developing Front-End Apps with React* course.

**Live application:** https://josemdasilvag-blip.github.io/e-plantShopping/

## Features

### Landing page
- Full-screen background image
- Company name — *Paradise Nursery*
- Paragraph describing the company (`AboutUs.jsx`)
- **Get Started** button that opens the product listing page

### Product listing page
- 30 house plants grouped into 5 categories: Air Purifying, Aromatic Fragrant,
  Insect Repellent, Medicinal, and Low Maintenance plants
- Every plant shows a thumbnail, name, description and price
- **Add to Cart** adds the plant to the cart, increases the header cart counter,
  and the button becomes disabled and reads *Added to Cart*
- Header with navigation (Home / Plants / Cart) and a cart icon showing the total
  number of items, updated live

### Shopping cart page
- Total cost of the whole cart and total number of plants in the cart
- Every plant in the cart shows its thumbnail, name, unit price, quantity and subtotal
- Increment (`+`) and decrement (`-`) buttons that update every total; decrementing the
  last unit removes the plant from the cart
- **Delete** button to remove a plant entirely
- **Continue Shopping** returns to the product listing
- **Checkout** shows a *Coming Soon* message

## Tech stack

- React 18 with functional components and hooks
- Redux Toolkit (`createSlice`) and React-Redux for global cart state
- Vite for the build and dev server
- `gh-pages` for deployment to GitHub Pages

## Redux state

The whole cart lives in a single slice, `src/CartSlice.jsx`:

| Action | Payload | Effect |
|---|---|---|
| `addItem` | plant object | Adds the plant with `quantity: 1`, or increments it if already in the cart |
| `removeItem` | plant name | Removes the plant from the cart |
| `updateQuantity` | `{ name, quantity }` | Sets the quantity of a plant already in the cart |

The store is configured in `src/store.js` and provided to the app in `src/main.jsx`.

## Project structure

```
src/
├── App.jsx          Landing page + toggle to the product listing
├── App.css          Landing page styles, including the background image
├── AboutUs.jsx      Paragraphs about the company
├── ProductList.jsx  Header, categories and product cards
├── CartItem.jsx     Shopping cart page
├── CartSlice.jsx    Redux slice for the cart
├── store.js         Redux store
└── main.jsx         Entry point, wraps the app in the Redux Provider
```

## Running locally

```bash
npm install
npm run dev
```

## Deploying to GitHub Pages

```bash
npm run deploy
```

Then, in the repository settings, set **Pages → Branch** to `gh-pages`.
