# MediStock - Project Metrics & Technical Overview

**Project Date:** April 2026  
**Repository:** https://github.com/ShashwatGohel/MediStock  
**Live App:** https://medi-stock-theta.vercel.app/

---

## 📊 Verified Project Statistics

### Code Metrics

| Metric                  | Value  | Details                                        |
| ----------------------- | ------ | ---------------------------------------------- | --------------- |
| **Total Lines of Code** | 11,845 | Backend: 2,933                                 | Frontend: 8,912 |
| **Backend Files**       | 40+    | Controllers, Models, Routes, Middleware, Utils |
| **Frontend Components** | 40+    | React.jsx pages & reusable components          |
| **API Endpoints**       | 46     | RESTful endpoints across 8 route files         |

### Database & Data

| Metric                  | Value     | Details                                                                                      |
| ----------------------- | --------- | -------------------------------------------------------------------------------------------- |
| **Medicine Catalog**    | 70+ items | Across 6 categories (Medicines, First Aid, Skincare, Baby Care, Devices, Fitness)            |
| **MongoDB Collections** | 11        | User, Medicine, Bill, Order, Store, Review, ChatRoom, Message, DailyRecord, VaultItem, Visit |
| **Data Models**         | 11        | Well-structured Mongoose schemas with validation                                             |

### Features Implemented

| Feature               | Status         | Details                                       |
| --------------------- | -------------- | --------------------------------------------- |
| **Geospatial Search** | ✅ Implemented | 5 km default radius, configurable up to 50 km |
| **Pagination**        | ✅ Implemented | 30-50 results per page (based on data type)   |
| **Real-Time Updates** | ✅ Implemented | Socket.io bidirectional communication         |
| **Authentication**    | ✅ Implemented | OTP email verification + JWT (1-day expiry)   |
| **Authorization**     | ✅ Implemented | Role-based access (User/Store/Admin)          |
| **Bulk Upload**       | ✅ Implemented | Excel file upload for medicines (xlsx)        |
| **Image Support**     | ✅ Implemented | Multer integration for file uploads           |

---

## 🛠️ Tech Stack

### Backend

- **Runtime:** Node.js (ES Modules)
- **Framework:** Express.js
- **Database:** MongoDB Atlas (Cloud)
- **Real-time:** Socket.io
- **Authentication:** JWT + Bcrypt
- **Email:** Nodemailer (Gmail SMTP)
- **File Processing:** XLSX parsing
- **Deployment:** Hosted on Vercel/Cloud

### Frontend

- **Framework:** React 18+
- **Styling:** Tailwind CSS + PostCSS
- **Build Tool:** Vite (Fast build process)
- **State Management:** React Context API
- **HTTP Client:** Fetch API
- **Real-time:** Socket.io Client
- **Animation:** Framer Motion
- **Icons:** Lucide React
- **Map:** Google Maps API integration
- **Deployment:** Vercel

### Database Optimization

- **Geospatial Indexes:** 2dsphere indexes on location fields (User & Store models)
- **Query Optimization:** Lean queries, field selection, aggregation pipelines
- **Indexing Strategy:** Indexed on storeId, email, category for faster lookups

---

## 🔌 API Endpoints Summary

### Authentication Routes (3 endpoints)

```
POST   /api/auth/signup
POST   /api/auth/login
POST   /api/auth/verify-otp
```

### Medicine Routes (10 endpoints)

```
POST   /api/medicines/add
POST   /api/medicines/bulk-upload
GET    /api/medicines/my-medicines
GET    /api/medicines/catalog
GET    /api/medicines/category-search
GET    /api/medicines/low-stock
GET    /api/medicines/expiring-medicines
GET    /api/medicines/reorder-suggestions
PATCH  /api/medicines/update/:id
DELETE /api/medicines/delete/:id
```

### Store Routes (10 endpoints)

```
GET    /api/stores/nearby
GET    /api/stores/all
GET    /api/stores/search
GET    /api/stores/saved
GET    /api/stores/profile
GET    /api/stores/:storeId
GET    /api/stores/:storeId/medicines
PUT    /api/stores/location
PUT    /api/stores/status
POST   /api/stores/toggle-save/:storeId
```

### Bill Routes (5 endpoints)

```
POST   /api/bills/create
GET    /api/bills/daily-stats
GET    /api/bills/my-bills
GET    /api/bills/visit-history
POST   /api/bills/increment-visit
```

### Order Routes (5 endpoints)

```
POST   /api/orders/request
GET    /api/orders/user-orders
GET    /api/orders/store-orders
PATCH  /api/orders/:id/status
DELETE /api/orders/:id
```

### Vault Routes (4 endpoints)

```
POST   /api/vault/add
GET    /api/vault/my-vault
PATCH  /api/vault/update/:id
DELETE /api/vault/delete/:id
```

### Chat Routes (4 endpoints)

```
GET    /api/chat/user/rooms
GET    /api/chat/store/rooms
GET    /api/chat/history/:roomId
POST   /api/chat/start
```

### Review Routes (3 endpoints)

```
GET    /api/reviews/store/:storeId
POST   /api/reviews/add
DELETE /api/reviews/:id
```

### Daily Record Routes (2 endpoints)

```
GET    /api/records/history
GET    /api/records/:date
```

---

## 📈 Performance Features

### Database Optimization

| Feature                  | Implementation                                  | Benefit                          |
| ------------------------ | ----------------------------------------------- | -------------------------------- |
| **Geospatial Indexing**  | 2dsphere index on location field                | Fast nearby store queries        |
| **Field Projection**     | `.select()` in queries                          | Reduced payload size             |
| **Lean Queries**         | `.lean()` for read-only operations              | Faster query execution           |
| **Aggregation Pipeline** | Complex analytics using $match, $group, $unwind | Efficient server-side processing |
| **Pagination**           | Limit & Skip on large datasets                  | Memory efficient                 |

### Frontend Optimization

| Feature                | Implementation                              |
| ---------------------- | ------------------------------------------- |
| **Dynamic Imports**    | Route-based code splitting with React       |
| **Image Lazy Loading** | Conditional rendering for mobile/desktop    |
| **Memoization**        | useMemo for expensive computations          |
| **Event Debouncing**   | Timer-based search optimization (mentioned) |
| **Vite Build**         | Optimized bundle with tree-shaking          |

---

## 🔐 Security & Authentication

### Authentication Flow

1. **Signup:** Password hashing with Bcrypt (10 salt rounds)
2. **Email Verification:** 6-digit OTP (10-minute expiry)
3. **Login:** JWT token generation (1-day expiry)
4. **Authorization:** Role-based middleware (user/store)

### Security Headers

- CORS configured for trusted origins
- JWT secret stored in .env
- Password hashing before storage
- OTP expiration validation

---

## 📱 User Features

### For Customers

- 🔍 Medicine search by name/category
- 🗺️ Nearby pharmacy locator (5-50 km radius)
- 🛒 Order management (pending → confirmed → delivered)
- 💾 Saved stores & prescription upload
- 💬 Real-time chat with store owners
- ⭐ Store reviews & ratings
- 📊 Order history & digital bills

### For Store Owners

- 📊 Dashboard with daily stats (sales, orders, visits)
- 💊 Inventory management (add/edit/delete/bulk upload)
- 📦 Order processing (accept/reject/confirm)
- 🧾 POS billing system
- 📈 Sales analytics (daily/weekly breakdown)
- 💬 Real-time customer chat
- 🔔 Low stock alerts

---

## 🚀 Scalability Considerations

| Aspect                   | Current            | Scalable?                               |
| ------------------------ | ------------------ | --------------------------------------- |
| **MongoDB Atlas**        | Cloud-hosted       | ✅ Yes (auto-scaling)                   |
| **Socket.io**            | Single server      | ⚠️ Needs Redis adapter for multi-server |
| **File Upload**          | Multer (in-memory) | ⚠️ Should use cloud storage (S3/GCS)    |
| **Geospatial Queries**   | Indexed properly   | ✅ Yes (efficient)                      |
| **Max Concurrent Users** | Not tested         | ~ 1000+ feasible with optimization      |

---

## 📋 Resume-Friendly Summary

**For Project Description:**

> MediStock is a full-stack Medical Inventory & Order Management System built with Node.js/Express and React. The platform connects local pharmacies with customers through a sophisticated geospatial search system, enabling medicine discovery and real-time order tracking.
>
> **Key Achievements:**
>
> - Developed 46 RESTful API endpoints with real-time communication (Socket.io)
> - Implemented geospatial indexing for efficient nearby store queries (5-50 km search radius)
> - Built role-based authentication system with JWT & OTP email verification
> - Created responsive React UI with 8,900+ lines of component code
> - Managed 11 MongoDB collections with optimized query patterns
> - Integrated Excel bulk upload for inventory management
> - Deployed on Vercel with MongoDB Atlas backend
> - **Total codebase: 11,845 lines** (Backend: 2,933 | Frontend: 8,912)

---

## 🔗 Important Links

| Resource         | URL                                        |
| ---------------- | ------------------------------------------ |
| **Live App**     | https://medi-stock-theta.vercel.app/       |
| **GitHub Repo**  | https://github.com/ShashwatGohel/MediStock |
| **Backend Port** | http://localhost:5005                      |
| **Frontend Dev** | http://localhost:5173                      |

---

_Last Updated: April 16, 2026_  
_All metrics verified from actual codebase_
