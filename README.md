# 🛒 **E-Commerce Platform with .NET 8, React & Redux** 🚀✨

This document provides an overview of our modern, full-featured **e-commerce application** built using **.NET 8** for the backend, **React** for the frontend, and **Redux** for state management. It delivers a seamless shopping experience with **real-time updates**, **responsive design**, and **secure payment integration**. 💻📱

---

## 🚀 **Technology Stack Overview** 🛠️

- ⚙️ **Backend:** ASP.NET Core 8
- 🌐 **Frontend:** React
- 📦 **State Management:** Redux (with Redux Toolkit for streamlined setup)
- 🔄 **Real-time Communication:** SignalR
- 🌟 **Styling:** Tailwind CSS
- 💳 **Payment Integration:** Stripe API
- 📂 **Caching & Data Storage:** Redis
- 🌩️ **Image Management:** Cloudinary (Effortless storage, optimization, and delivery of product images)

---

## 🎯 **Key Features Overview** 🌟

- 🛕️ **Product Management:** Browse, search, and filter products effortlessly.
- 🔄 **Real-time Updates:** Instant updates on orders and notifications via SignalR.
- 📦 **State Management:** Efficient global state handling with Redux for a predictable and scalable app architecture.
- 💳 **Secure Payments:** Stripe integration for seamless and secure transactions. Refunds and coupon codes included.
- 🔒 **Authentication & Authorization:** Secure user authentication and role-based access.
- 📊 **Order Tracking:** Admin dashboard for a real-time inventory system.
- 📂️ **User Cart Management:** Redis is used to store user cart data efficiently.
- ⚡ **Request Caching:** Redis caches frequent requests to improve performance and reduce server load.
- 🌩️ **Image Optimization:** Cloudinary ensures fast and optimized delivery of high-quality product images.

---

## 🛠️ **Setup Instructions** 📝

To run this application locally, please follow the steps below:

### **🩰 Prerequisites** ⚡

Ensure you have the following installed:

1. 🐳 **Docker**
2. 🛠️ **.NET SDK v8**
3. 📦 **NodeJS (v20.11.1 or later)** _(Optional for React dev mode)_

### **👅 Step 1: Clone the Repository** 🔀

```bash
git clone https://github.com/BernieTv/.NET-Eccomerce-with-React
cd .NET-Eccomerce-with-React
```

### **📦 Step 2: Restore Dependencies** 🔄

```bash
# From the solution folder
 dotnet restore

# Navigate to the React client folder
cd client
npm install
```

### **💳 Step 3: Stripe Configuration** 🔑

To enable payment functionality, set up your **Stripe keys**:

1. Create an `appsettings.json` file in the **API folder**:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "StripeSettings": {
    "PublishableKey": "pk_test_REPLACEME",
    "SecretKey": "sk_test_REPLACEME",
    "WhSecret": "whsec_REPLACEME"
  },
  "AllowedHosts": "*"
}
```

2. Set up **Stripe CLI** for local webhook forwarding:

```bash
stripe login
stripe listen --forward-to https://localhost:5001/api/payments/webhook -e payment_intent.succeeded
```

### **🌩️ Step 4: Cloudinary Configuration** 🖼️

To enable image management:

1. Sign up for a **Cloudinary account**.
2. Retrieve your **Cloud Name**, **API Key**, and **API Secret**.
3. Add the configuration to the `appsettings.json` file in the **API folder**:

```json
"CloudinarySettings": {
  "CloudName": "your-cloud-name",
  "ApiKey": "your-api-key",
  "ApiSecret": "your-api-secret"
}
```

4. Use Cloudinary for uploading and delivering product images in the backend.

### **🐘 Step 5: Start Database Services** 💄

The app requires **SQL Server** and **Redis**. Start these services using **Docker**:

```bash
docker compose up -d
```

Ensure no conflicting services are running on **port 1433** (SQL Server) or **port 6379** (Redis).

### **🚦 Step 6: Start the Application** ▶️

Run the **backend API**:

```bash
cd API
dotnet run
```

Access the app locally: 🌍 [https://localhost:5001](https://localhost:5001)

### **💻 Step 7: Run React Frontend in Development Mode** 🖥️

Start **React Dev Server**:

```bash
cd client
npm run dev
```

Browse to: 🌐 [https://localhost:3000](https://localhost:3000)

### **🛡️ Step 8: Test Payments** 💵

Use **Stripe test cards** available [here](https://docs.stripe.com/testing#cards) for payment simulation.

---

## 📄 **License** 📜

This project is licensed under the **MIT License**. 📝
