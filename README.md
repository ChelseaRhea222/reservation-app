# Restaurant Reservation Seat Map Web App

An interactive restaurant floor‑plan reservation system that lets users
select seats directly from a live visual layout.

This project demonstrates:

• Frontend UI/UX design\
• Dynamic seat rendering\
• Real‑time availability polling\
• Smart reservation rules\
• Backend API integration

Built using **pure HTML + CSS + JavaScript (no frameworks)**.

------------------------------------------------------------------------

# Demo

Open locally:

reservation_app.html

Or deploy to any static host:

• GitHub Pages\
• NixiHost\
• Bluehost\
• Netlify\
• Vercel

No build step required.

------------------------------------------------------------------------

# Features

## Interactive Floor Plan

-   Visual restaurant layout (Kitchen, Bar, Hightop, Dining, Booth,
    Patio)
-   Clickable seats/tables
-   Auto‑scaled map fits any screen
-   Mobile responsive

## Reservation Controls

-   Party size selector
-   Date picker
-   15‑minute time slots only
-   Business hours enforced (3pm--10pm)

## Smart Validation Rules

-   Party size → allowed areas
-   Capacity enforcement
-   Stools vs tables rules
-   Prevents invalid combinations

## Live Updates

-   Polls backend every 2 seconds
-   Real‑time availability refresh

## Visual Feedback

Green → available\
Yellow → selected\
Red → reserved\
Gray → disabled

------------------------------------------------------------------------

# Tech Stack

Frontend: - HTML - CSS - Vanilla JavaScript

Backend (example): - PHP API - Oracle / MySQL / any database

Hosting: - Static hosting (NixiHost/Bluehost/etc)

No frameworks. No dependencies. Single file app.

------------------------------------------------------------------------

# Project Structure

/ ├── reservation_app.html ← Entire app (HTML + CSS + JS) ├── assets/ │
└── icons/ │ └── stool.svg └── README.md

Everything runs from ONE file.

------------------------------------------------------------------------

## Update API endpoints

Inside reservation_app.html:

const CONFIG = { availabilityUrl:
'https://yourdomain.com/api/availability.php', reserveUrl:
'https://yourdomain.com/api/reserve.php' };

## 3. Run

Double‑click reservation_app.html

Done.

------------------------------------------------------------------------

# Backend API Requirements

## GET availability

GET /api/availability.php?datetime=ISO_DATE&party_size=2

Response:

\[ { "id": 12, "area": "dining", "kind": "tableRound", "capacity": 4,
"x_pos": 40, "y_pos": 22, "size_val": 4, "rotation_deg": 0,
"available_for_selected_time": true }\]

------------------------------------------------------------------------

## POST reserve

POST /api/reserve.php

Body:

{ "datetime": "2026-02-10T19:00:00.000Z", "party_size": 4, "seat_ids":
\[12\] }

Response:

{ "success": true }

------------------------------------------------------------------------

# Seat Types

stool → single bar seat\
tableRound → round table\
tableSquare → square table\
booth → booth seating

Rules: • Party 1 → stool only\
• Party 2--4 → stools OR 1 table\
• Party 5+ → table only\
• No mixing stools + tables

------------------------------------------------------------------------

# Styling / Customization

## Change seat size

Inside JS:

const multiplier = 12;

Increase → bigger seats\
Decrease → smaller seats

------------------------------------------------------------------------

## Change colors

CSS:

.seat.available { background:#009688; } .seat.selected {
background:#ffc107; } .seat.reserved { background:#f44336; }

------------------------------------------------------------------------

## Change shapes

.seat.stool { border-radius:50%; } .seat.booth { border-radius:12px; }
.seat.hightop { border-radius:6px; }

------------------------------------------------------------------------

# Responsive Layout

Desktop: Left controls + right floor map

Mobile: Stacked layout

Map auto‑scales to fit screen\
Action bar always visible

------------------------------------------------------------------------

# Architecture

User ↓ HTML UI ↓ JavaScript state ↓ API (availability/reserve) ↓
Database

Frontend is stateless. Backend controls truth.




