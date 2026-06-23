# Cooking Masterclass Catalogue

A responsive Vue 3 single-page catalogue prototype for Cooking Masterclass.

## Overview

This app displays curated cooking workshops in a clean catalogue layout. Users can view course details, see whether a session is available or sold out, and save sessions to a wishlist. The wishlist count updates in real time so the platform can later expand into checkout and login features.

## Features

- Responsive course cards with chef name, price, and skill level
- Sold out indicator for unavailable sessions
- Wishlist button that saves favorites and updates the header count
- Clean branding with minimal color palette and mobile-friendly layout

## Installation

```sh
npm install
```

## Run locally

```sh
npm run dev
```

Then open the local Vite URL shown in the terminal.

## Build for production

```sh
npm run build
```

## Notes

- The catalogue renders dynamically from a course list in `src/App.vue`
- Saved courses are tracked in the wishlist array and displayed in the header
- Course cards use `src/components/icons/CourseCard.vue`

## Screenshot

Add a screenshot of the interface here after running the app and capturing the page.
