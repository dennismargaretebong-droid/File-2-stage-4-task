
SYSTEM ARCHITECHURE FOR REP DASH

The blue print for this task is to create the necessary awareness for the already existing product.which entails the following;

Show work flow of the app from order to delivery.

Managing the current services to reduce engineering cost.

Isolate parts in the currents app that is risky.

Instrument every flow and take note of current changes made for further prioritization.

FRONTEND

Customer + Drivers mobile app: React Native like Expo(single code base and fast iteration)
Merchant/riders and admin panels: React + Typescript or (Next.js for quick SSR if needed)
Reason for choosing react native framework is because this feature is mostly used for large scale work that is prone to heavy traffic and real time activities.

BACKEND

Modular monolith first architecture: Node.js + NestJS or Express + TypeScript (single service initially, split later) Realtime: Socket.IO for prototype

Reason for choosing this backend tool is because it's faster in delivery and good for iterations.

DATABASE STACK

Primary DB: PostgreSQL (PostGIS extension if geospatial queries needed).

Cache / pub-sub / jobs: Redis (managed Redis) pub/sub and simple queues.

Object storage: S3 (AWS) or DigitalOcean Spaces for images and receipts.

THIRD PARTIES

For 3rd parties like maps, payment platforms and sms notification platforms we will maintain the existing ones.


Maps:Google Maps (directions)Payments:(Paystack, Flutterwave)

Push and messaging: Firebase Cloud Messaging and MSG91 for SMS.

HOW COMPONENTS COMMUNICATE

| Customer App |Driver App | Merchant App|

| HTTPS(REST)|HTTPS / WS | HTTPS (REST)|

[Backend Monolith - API]

| Authorization | Orders | Tracking |

| Push | Payments| Notifications|

|[Postgres + PostGIS] <--> [Redis (pub/sub, cache, queue)

[S3 Storage]|

[Map API] [Payment Gateway] [FCM / SMS])

Mobile/web:Backend over HTTPS (REST/GraphQL).

Realtime order and tracking updates via Socket.IO (driver to backend to customer). 

Socket server uses Redis pub/sub for multi-instance support.

Backend calls Map API for routing/ETA when assigning drivers (cached). Payments handled by Payments component via gateway webhooks to backend.


WHY MY APPROACH IS TECHNICALLY VISIBLE

In the cause of my research i noticed that other online delivery and ordering apps like chowdeck and Glovo who use same architechural framework as listed above are doing well and visible in the market, this is why i think using this architechural framework is technically visible and below are my reasons;

Using React Native to redesign the app is mature as it is mostly used for food and delivery app.

Postgres/Redis/S3 helps in reducing opertions burden while vadilating market feet.

Modular Molinth first this feature mostly used by backend developers help in reducing coordination friction and accelerates fast delivery.

Redis adapter is a standard data source with an, horizontally-scaleable approach used by many delivery and rideshare systems.
