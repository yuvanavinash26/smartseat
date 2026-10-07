# SmartSeat

An interactive, dependency-free restaurant reservation demonstration.

## Run
Double-click `index.html` to open the app in your browser. Alternatively, run `python -m http.server 8080` from this folder and visit http://localhost:8080.

No install or build step is required. An optional Google font is downloaded; the app falls back to Arial offline.

## Included
- Cinematic landing page and scroll-linked seating explanations
- Animated table evaluation and adjacent-table grouping
- Six-step reservation flow with 90-minute conflict checks
- Indoor/outdoor seating and capacity-based allocation
- Interactive staff console, table inspector, arrivals, walk-ins and checkout
- FIFO suitable-party waitlist and local analytics
- Browser-local persistence and JSON export
- Responsive layout, keyboard focus styles and reduced-motion support

## Data and algorithms
Data stays in localStorage under `smartseat-v1`. Reservations are not sent to a restaurant. Demo floor occupancy and the illustrative occupancy chart are labeled.

Allocation enumerates single tables and configured adjacent pairs, filters conflicts using half-open time intervals, then minimizes unused seats. Equal fits prefer T04/T05 to demonstrate the signature interaction. This small demo uses linear interval scans rather than a balanced interval tree. Group membership is stored explicitly rather than a DSU: ordinary Union-Find cannot split on checkout. The UI presents the UNION concept without claiming a production DSU implementation.

Physical occupancy blocks today's allocations conservatively; future-date bookings are supported. Service stations are disabled. Indoor waitlist seating checks a 90-minute window from the current time.

## Production boundaries
No backend, authentication, payments, notifications or real restaurant booking integration is included. Future backend work should add transactional conflict protection, staff permissions, timezone-aware timestamps, and event-based analytics.

## DSA playground and visual upgrade
Open the DSA playground link in navigation. It includes an executable augmented interval BST with traversal and pruning, a separate Union-Find sandbox with union by size and path compression, and stepwise capacity allocation. Use Next step, Back, Auto-play and Reset. These educational examples do not modify restaurant data. The reservation app still uses linear conflict checks and explicit table groups.

The design adds animated ambient lighting, brighter typography, dimensional table surfaces and a dedicated playground layout. Motion respects reduced-motion preferences. Files premium.css and intelligence.js must remain alongside index.html. The original single-file version is preserved as index.original.html.
