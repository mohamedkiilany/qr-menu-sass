# QR Menu SaaS Project Specification

## Project Name
QR Menu SaaS

---

# Project Overview

A modern SaaS platform for restaurants and cafes that replaces traditional paper menus with QR-based digital ordering.

Customers scan a QR code placed on the table and can:
- Browse the menu
- Add items to cart
- Place orders
- Call the waiter
- Track order status

Restaurant owners can:
- Manage products and categories
- Monitor live orders
- Manage tables and QR codes
- View analytics and reports

Kitchen staff can:
- View live incoming orders
- Update order status
- Track preparation queue

---

# Business Goals

- Reduce paper menu costs
- Reduce ordering mistakes
- Improve customer experience
- Speed up order handling
- Provide digital transformation for small restaurants and cafes
- Generate recurring monthly subscription revenue

---

# System Type

Multi-tenant SaaS platform.

Each restaurant has:
- Its own dashboard
- Its own menu
- Its own tables
- Its own staff
- Its own orders

---

# Target Users

## 1. Customers
Customers sitting inside restaurants.

### Permissions
- Browse menu
- Search products
- Add to cart
- Place order
- Call waiter
- Track order status

---

## 2. Restaurant Admin
Restaurant owner or manager.

### Permissions
- Manage products
- Manage categories
- Manage tables
- Generate QR codes
- Manage orders
- Manage staff
- View analytics

---

## 3. Kitchen Staff
Kitchen employees.

### Permissions
- View incoming orders
- Update order status
- Mark orders as ready

---

# Recommended Tech Stack

## Frontend
- Flutter
- Flutter Web
- Responsive UI

## Backend
- Firebase Authentication
- Cloud Firestore
- Firebase Storage
- Firebase Cloud Messaging
- Firebase Hosting

## State Management
Recommended:
- Riverpod
OR
- Bloc

## Architecture
Clean Architecture + Feature-based Structure

---

# Project Modules

# 1. Authentication Module

## Features
- Admin login
- Staff login
- Restaurant registration
- Password reset
- Session persistence

## Firebase
- Firebase Auth

---

# 2. Restaurant Management Module

## Features
- Create restaurant profile
- Upload logo
- Add restaurant information
- Configure restaurant settings

## Fields
- Restaurant name
- Description
- Phone number
- Address
- Logo
- Currency
- Opening hours

---

# 3. Table & QR Module

## Features
- Create tables
- Generate QR code for each table
- Print QR codes
- Unique QR URL per table

## Example URL
https://domain.com/menu/restaurant-id/table-5

## QR Flow
Customer scans QR -> Opens menu page -> Table detected automatically

---

# 4. Menu Module

## Features
- Categories
- Product listing
- Product search
- Product details
- Product images
- Availability status

## Product Fields
- Name
- Description
- Price
- Image
- Category
- Availability
- Preparation time

## Categories Examples
- Drinks
- Main Courses
- Desserts
- Hot Drinks
- Cold Drinks

---

# 5. Cart Module

## Features
- Add to cart
- Remove from cart
- Increase/decrease quantity
- Add notes
- Calculate totals

## Notes Examples
- No sugar
- Extra cheese
- No onions

---

# 6. Orders Module

## Features
- Place order
- Real-time order updates
- Order history
- Order status tracking

## Order Statuses
- Pending
- Accepted
- Preparing
- Ready
- Delivered
- Cancelled

## Order Fields
- Table number
- Customer notes
- Order items
- Total price
- Timestamp
- Status

---

# 7. Kitchen Dashboard Module

## Features
- Real-time incoming orders
- Order queue
- Change order status
- Preparation timer

## UI Requirements
- Large readable cards
- Simple layout
- Real-time updates
- Touch-friendly interface

---

# 8. Admin Dashboard Module

## Features
- Manage menu
- Manage orders
- Manage tables
- Analytics
- Staff management
- Revenue tracking

## Dashboard Widgets
- Total orders
- Revenue today
- Active orders
- Most sold items
- Peak hours

---

# 9. Analytics Module

## Features
- Daily revenue
- Weekly revenue
- Monthly revenue
- Most ordered items
- Order count
- Average order value

## Charts
- Revenue chart
- Orders chart
- Product performance chart

---

# 10. Notifications Module

## Features
- New order notifications
- Order ready notifications
- Admin alerts

## Firebase
- Firebase Cloud Messaging

---

# Future Features

## Phase 2
- Online payment
- Loyalty system
- Customer accounts
- Multi-language support
- AI recommendations
- Delivery integration
- Waiter mobile app
- Inventory management
- Coupon system
- Reservation system

---

# Suggested Folder Structure

```text
lib/
│
├── core/
│   ├── constants/
│   ├── theme/
│   ├── utils/
│   ├── services/
│   └── widgets/
│
├── data/
│   ├── models/
│   ├── repositories/
│   └── datasources/
│
├── features/
│   ├── auth/
│   ├── restaurant/
│   ├── menu/
│   ├── cart/
│   ├── orders/
│   ├── kitchen/
│   ├── admin/
│   ├── analytics/
│   └── notifications/
│
├── routes/
├── app.dart
└── main.dart
```

---

# Firestore Database Design

# Collections

## restaurants

```json
{
  "id": "",
  "name": "",
  "description": "",
  "logo": "",
  "phone": "",
  "address": "",
  "ownerId": "",
  "createdAt": ""
}
```

---

## tables

```json
{
  "id": "",
  "restaurantId": "",
  "tableNumber": 1,
  "qrCode": "",
  "createdAt": ""
}
```

---

## categories

```json
{
  "id": "",
  "restaurantId": "",
  "name": "Drinks",
  "image": ""
}
```

---

## products

```json
{
  "id": "",
  "restaurantId": "",
  "categoryId": "",
  "name": "Latte",
  "description": "",
  "price": 120,
  "image": "",
  "available": true,
  "prepTime": 10
}
```

---

## orders

```json
{
  "id": "",
  "restaurantId": "",
  "tableId": "",
  "items": [],
  "total": 0,
  "status": "pending",
  "notes": "",
  "createdAt": ""
}
```

---

# API / Service Responsibilities

## Auth Service
- Login
- Logout
- Register
- Reset password

## Product Service
- CRUD products
- Fetch products
- Search products

## Orders Service
- Create order
- Update order status
- Stream live orders

## Analytics Service
- Revenue calculation
- Reports generation

---

# UI/UX Requirements

## Design Style
- Modern
- Minimal
- Fast
- Responsive
- Dark mode support

## Main Colors
Suggested:
- Black
- White
- Orange
OR
- Dark Gray + Gold

## UX Requirements
- Simple ordering flow
- Maximum 3 clicks to place order
- Fast loading
- Smooth animations

---

# Responsive Platforms

## Customer Side
- Mobile-first responsive web app

## Admin Dashboard
- Desktop + tablet optimized

## Kitchen Dashboard
- Tablet landscape optimized

---

# Security Requirements

- Firebase Rules
- Restaurant data isolation
- Role-based access
- Protected admin routes
- Input validation

---

# Performance Requirements

- Real-time order updates
- Lazy loading
- Optimized images
- Cached menu data
- Fast startup time

---

# SaaS Subscription Plans

## Basic
- Up to 20 products
- Single branch
- Basic analytics

## Pro
- Unlimited products
- Multiple branches
- Full analytics
- Notifications

## Enterprise
- Custom features
- Dedicated support
- White-label solution

---

# Development Phases

# Phase 1 - MVP

## Build First
- Authentication
- Menu system
- QR system
- Orders system
- Kitchen dashboard
- Admin dashboard

Goal:
Get first restaurant customer.

---

# Phase 2

## Add
- Payments
- Analytics
- Notifications
- Loyalty system

---

# Phase 3

## Scale
- Multi-branch support
- Mobile apps
- AI features
- Delivery system

---

# Recommended Flutter Packages

## Core Packages
- go_router
- flutter_riverpod
- firebase_core
- firebase_auth
- cloud_firestore
- firebase_storage
- firebase_messaging
- cached_network_image
- flutter_animate
- qr_flutter
- mobile_scanner

---

# Suggested Screens

# Customer Screens
- Splash Screen
- Menu Screen
- Product Details
- Cart Screen
- Order Tracking
- Order Success

---

# Admin Screens
- Login
- Dashboard
- Products Management
- Categories Management
- Orders Management
- Analytics
- Tables Management

---

# Kitchen Screens
- Live Orders
- Order Details
- Preparation Queue

---

# Full Workflow

```text
Restaurant creates account
        ↓
Restaurant adds products/categories
        ↓
Restaurant creates tables
        ↓
System generates QR codes
        ↓
Customer scans QR
        ↓
Menu opens automatically
        ↓
Customer places order
        ↓
Kitchen receives live order
        ↓
Kitchen updates status
        ↓
Customer receives order
```

---

# Important Notes

- Start simple.
- Focus on speed and reliability.
- Do not overbuild the first version.
- Get real restaurant feedback early.
- Prioritize user experience.
- Optimize for low internet speed.

---

# MVP Priority Checklist

## Highest Priority
- QR scanning
- Menu loading
- Cart
- Order creation
- Kitchen live updates
- Admin product management

## Medium Priority
- Analytics
- Notifications
- Reports

## Low Priority
- Payments
- Loyalty
- AI features
- Delivery integration

---

# Suggested Initial Timeline

## Week 1
- Project setup
- Firebase setup
- Authentication
- Basic UI

## Week 2
- Menu system
- Products
- Categories

## Week 3
- Cart
- Orders
- Firestore integration

## Week 4
- Kitchen dashboard
- Admin dashboard
- QR generation

## Week 5
- Testing
- Deployment
- Demo preparation

---

# Final Goal

Build a scalable restaurant ordering SaaS platform that can start locally and scale to multiple cities and restaurants.

