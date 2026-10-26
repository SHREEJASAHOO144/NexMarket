# 🛍️ NexMarket — Dual-Role Digital Marketplace

NexMarket is a web-based digital marketplace designed to connect customers and vendors on a single platform. It allows customers to explore stores, browse products, manage shopping carts, save favorite items, and review their order history. Vendors can create and manage their stores, organize product listings, and maintain their storefront information.

The application features a modern, responsive interface with a dark theme, neon-inspired gradients, glassmorphism effects, and interactive dashboard components. Its dual-role account concept allows users to register as customers, vendors, or both, bringing shopping and selling experiences together in one application.

## ✨ Key Features

### 🔐 User Authentication & Account Management
- User registration and login through backend API endpoints.
- Support for customer, vendor, and dual-role accounts.
- Profile page displaying account information and role details.
- Role-specific dashboard navigation.

### 🛒 Customer Shopping Experience
- Browse available stores and their product listings.
- Explore products with images, prices, and store information.
- Add products to the shopping cart and manage quantities.
- Maintain a wishlist of favorite products.
- Move wishlist items to the cart.
- Review previous orders and add previously purchased items back to the cart.
- View favorite stores and shopping statistics based on order history.

### 🏪 Vendor Store Management
- Create and update store profiles.
- Specify store names, categories, locations, descriptions, and images.
- Manage product listings and prices.
- Access store information and product counts through the profile dashboard.
- Use category-based product suggestions to simplify product entry.

### 📦 Order & Delivery Management
- Place orders through backend API endpoints.
- Store order information, purchased items, quantities, totals, and payment-method labels.
- View order history and order-related transaction summaries.
- Access a delivery-tracking interface with an interactive map, driver marker, delivery information, and estimated arrival display.

### 📊 Shopping Insights & Personalization
- View frequently ordered stores.
- Track the number of orders, items purchased, and spending by store.
- Save favorite products in a wishlist.
- Review profile and vendor store statistics.

### 🎨 User Interface & Design
- Dark-themed interface with blue, purple, and green accent colors.
- Glassmorphism-inspired cards and navigation elements.
- Gradient effects, hover animations, and interactive components.
- Responsive dashboard layouts.
- Custom illustrations and product imagery.
- Interactive delivery map powered by Leaflet and map tiles from CARTO/OpenStreetMap.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend application logic |
| Flask | REST API and server-side routing |
| Flask-CORS | Cross-origin communication between frontend and backend |
| SQLite | Persistent relational database |
| HTML5 | Web page structure |
| CSS3 | Styling, layouts, animations, and responsive design |
| JavaScript | Client-side interactions and API requests |
| Leaflet.js | Interactive delivery map |
| OpenStreetMap / CARTO | Map tiles and geographic visualization |
| Gunicorn | Production WSGI server |
| Render | Deployment configuration |

## 🏗️ Application Architecture

NexMarket uses a frontend-backend architecture.

- **Frontend:** HTML, CSS, and JavaScript provide the user interface and interactive shopping features.
- **Backend:** Flask exposes REST API endpoints for authentication, stores, products, orders, and wishlists.
- **Database:** SQLite stores users, stores, products, orders, order items, and wishlist entries.
- **Deployment:** A Render configuration defines the Python web service and uses Gunicorn to serve the Flask application.

## 🗂️ Main Project Components

- `index.html` — Main landing page and account entry point.
- `customer.html` — Customer shopping dashboard.
- `vendor.html` — Vendor store and product management.
- `profile.html` — User profile and account information.
- `cart.html` — Shopping cart interface.
- `wishlist.html` — Saved products and wishlist management.
- `reorders.html` — Order history and reordering interface.
- `transactions.html` — Transaction history display.
- `delivery.html` — Delivery tracking interface.
- `mostly-shopped.html` — Frequently ordered store insights.
- `app.py` — Flask backend and API endpoints.
- `marketplace.db` — SQLite database.
- `style.css` — Main application styling.
- `dashboard.css` — Shared dashboard styling.
- `script.js` — Landing page interactions and authentication requests.
- `render.yaml` — Render deployment configuration.
- `requirements.txt` — Python dependencies.

## ⚙️ Getting Started

### Prerequisites

- Python 3.10 or later recommended.
- pip (Python package installer).
- A modern web browser.
- Visual Studio Code with the Live Server extension, or another local frontend web server.

### 1. Clone the Repository

```bash
git clone https://github.com/SHREEJASAHOO144/thryve-app.git
cd thryve-app
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

On macOS or Linux:

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the Flask Backend

```bash
python app.py
```

The backend starts on port `5000` and is configured to listen on `0.0.0.0`.

### 5. Open the Frontend

Open the project folder in Visual Studio Code, start Live Server from `index.html`, and open the resulting local URL in your browser.

The frontend JavaScript currently makes API requests to `http://localhost:5000`, so the backend must be running locally for those requests to work.

**Database note:** The application uses `marketplace.db`. Keep the database file in the expected working directory when running the backend. The supplied application initializes its tables when the database file does not exist.

## 🔌 Backend API Overview

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Register a user |
| POST | `/api/auth/login` | Authenticate a user |
| GET | `/api/stores` | Retrieve stores and products |
| POST | `/api/stores` | Create or update a store and its products |
| GET | `/api/vendor/<vendor_id>/stores` | Retrieve a vendor's stores |
| POST | `/api/orders` | Create an order |
| GET | `/api/users/<user_id>/orders` | Retrieve a user's orders |
| GET | `/api/users/<user_id>/wishlist` | Retrieve a user's wishlist |
| POST | `/api/users/<user_id>/wishlist` | Add a wishlist item |
| DELETE | `/api/users/<user_id>/wishlist` | Remove a wishlist item |

## 🚀 Deployment

The repository includes a `render.yaml` configuration for deploying the Flask backend on Render.

The configured start command is:

```bash
gunicorn app:app
```

For deployment, configure the service with the required Python dependencies and ensure the frontend's API base URL points to the deployed backend rather than `localhost`. Configure persistent storage for SQLite if database data must survive service restarts or redeployments.

## 🔮 Future Enhancements

- Integrate a secure payment gateway for actual payment processing.
- Implement real-time GPS-based delivery tracking and route updates.
- Add product reviews, ratings, and vendor feedback.
- Improve authentication security with password hashing and authorization checks.
- Introduce advanced shopping analytics and sales reports.
- Add automated tests and API documentation.
- Improve production database management and deployment security.

## ⚠️ Current Implementation Notes

- The delivery interface uses a map with generated marker positions; real-time driver GPS tracking is not established by the supplied code.
- Transaction entries are derived from order information. A live payment gateway integration is not established by the supplied backend.
- The frontend uses local storage for some client-side state and fallback data.
- The current backend contains basic authentication endpoints; production deployment should include stronger password storage, validation, and access controls.

## 🎯 Project Objective

The objective of NexMarket is to demonstrate how a full-stack marketplace can bring customer shopping and vendor store management together through a unified platform. It combines frontend interface design, JavaScript interactions, REST API development, relational database operations, and deployment configuration in one project.

## 👩‍💻 Project Information

**Project:** NexMarket — Dual-Role Digital Marketplace  
**Category:** Full-Stack Web Development  
**Backend:** Python and Flask  
**Database:** SQLite  
**Frontend:** HTML, CSS, and JavaScript

