# Order Management Tool

## Overview

The Order Management Tool is a web application designed to manage orders for a restaurant. It allows users to place orders, view their order history, and download invoices. Employees can manage orders, and administrators can manage users and view all orders.

# Hosted website preview

`https://megumiramenrestaurant.vercel.app/`

---

## Project Structure

The project is structured as follows:

- `app/`: Contains the main application code.
  - `api/`: Contains API route handlers.
    - `auth/`: Authentication routes.
      - `register`:
      - `orders/`: Order-related routes
      - `users/`: User-related routes.
      - `menu`: All positions form the shop
  - `cart`: Cart for product storage
  - `checkout`: Transaction finalization
  - `contexts/`: Context providers for global state management.
  - `employeePanel/`: Employee panel page.
  - `adminPanel/`: Admin panel page.
  - `unauthorized`: Unauthorized access
  - `orders/`: Order-related routes
  - `thank-you/`: Thank you page after placing an order.
  - `not-found.js`: Custom 404 page.
  - `menu`: All positions form the shop
  - `login`: Handle login
  - `register`: Handle register
- `components/`: Reusable React components.
- `lib/`: Contains utility libraries.
  - `prisma.js`: Prisma client setup.
- `public/`: Public assets.

---

## Technologies Used

- **JavaScript**: The primary programming language.
- **React**: For building the user interface.
- **Next.js**: For server-side rendering and API routes.
- **Prisma**: For database ORM.
- **Next-Auth**: For authentication.
- **React Toastify**: For notifications.
- **Tailwind CSS**: For styling.

---

## How It Works

### User Roles

- **Customer**: Can place orders, view order history, and download invoices.
- **Employee**: Can manage orders (change status, cancel).
- **Admin**: Can manage users (add, edit, delete) and view all orders.

### Authentication

The application uses Next-Auth for authentication. Users can log in with their email and password. The session is managed using cookies.

### Order Management

- **Placing Orders**: Customers can add items to their cart and place orders. The order details are saved in the database.
- **Viewing Orders**: Customers can view their order history. Employees and admins can view all orders.
- **Managing Orders**: Employees can change the status of orders (e.g., from pending to preparing) and cancel orders.

### User Management

Admins can manage users through the admin panel. They can add new users, edit user roles, and delete users.

---

## Test Users

You can use the following test users to log in and explore the application:

- **Employee**
  - Email: `employee@employee.com`
  - Password: `employee`
- **Admin**
  - Email: `admin@admin.com`
  - Password: `admin`

---

## Getting Started

### Prerequisites

- Node.js (v18 or higher)
- npm (v9 or higher)
- MariaDB (or any other database supported by Prisma)

### Installation

1. Clone the repository:
   
       git clone https://github.com/AdamW03/orderManagementTool
       cd order-management-tool
    Install dependencies:
   
       npm install

    Set up the database:
        Create a .env file in the root directory and add your database connection string:

        env. DATABASE_URL="mysql://user:password@localhost:5432/order_management"

   Run Prisma migrations:

        npx prisma migrate dev --name init
   
   Run Prisma Seed:
   
        npm prisma db seed```
   
    Start the development server:

       npm run dev

    Open your browser and navigate to http://localhost:3000.

### API Endpoints Authentication

    POST /api/auth/signin: User login.

    POST /api/auth/signout: User logout.

### Orders

    GET /api/orders?type=fall: Get all orders (for employees and admins).

    GET /api/orders?type=all: Get all orders for the logged-in user.

    GET /api/orders?type=latest: Get the latest order for the logged-in user.

    POST /api/orders: Create a new order.

    PATCH /api/orders/:id: Update the status of an order.

### Users

    GET /api/users: Get all users (for admins).

    POST /api/users: Create a new user (for admins).

    PATCH /api/users/:id: Update a user (for admins).

    DELETE /api/users/:id: Delete a user (for admins).

### Environment Variables The following environment variables are required:

    DATABASE_URL: The connection string for your database.

    NEXTAUTH_SECRET: A secret key for Next-Auth (e.g., generate using openssl rand -base64 32).

    NEXTAUTH_URL: The base URL of your application (e.g., http://localhost:3000).
