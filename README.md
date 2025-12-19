# 🛒 Christian's EasyShop 

## ⭐ 

EasyShop is a **full-stack Java e-commerce application** developed as a capstone project to demonstrate **industry-ready coding practices**, clean architecture, and thoughtful user experience design. The project goes **beyond minimum requirements** by implementing secure authentication, user-specific data handling, and a polished frontend experience aligned with real-world retail applications.



* Clean, well-documented code
* Clear separation of concerns (Controller / DAO / Model)
* Secure user-based functionality
* Professional README documentation
* Attention to UX, structure, and maintainability

---

## 📖 Project Description

EasyShop simulates a real online shopping platform where authenticated users can browse products, filter results, manage a shopping cart, and securely complete purchases.

The application was designed to mirror professional e-commerce workflows while maintaining readability and extensibility for future enhancements.

---

## ⭐ Key Features

### 🛍 Product Browsing

* Browse all available products
* Filter products by:

    * Category
    * Minimum price
    * Maximum price
* Grid-based layout for clear product display

Products are retrieved using the **DAO pattern**, ensuring database access remains isolated from business logic.

---

### 🗂 Category Filtering

* Categories stored in the database
* Products linked to categories by ID
* Real-time filtering via REST endpoints

---

### 🛒 Shopping Cart

* Add products to cart
* Remove products from cart
* View real-time cart totals
* Cart data is tied to the authenticated user

This ensures each user maintains an independent shopping experience.

---

### 🔐 Authentication & Security

* JWT-based authentication
* Secure endpoints using Spring Security
* User-specific access to carts and profiles

Only authenticated users can modify cart data or checkout.

---

## 🧠 Technical Architecture

### Backend

* Java
* Spring Boot
* RESTful APIs
* DAO pattern for persistence
* MySQL database
* JWT authentication

Each layer has a single responsibility, promoting readability and long-term maintainability.

---

## ⭐ Interesting Code: Secure Profile Update Endpoint

One of the most important parts of EasyShop is the **user profile system**, which ensures data isolation and secure access to user-specific resources.

The User Profile logic:

* Extracts the authenticated user from the JWT token
* Retrieves profile information tied to that user
* Prevents access to other users’ data

#### The following controller method handles updating a user’s profile using an HTTP PUT request.

```java
@PutMapping
public Profile updateProfile(Principal principal, @RequestBody Profile profile) {

    String userName = principal.getName();
    User user = userDao.getByUserName(userName);

    // Force the profile to belong to the authenticated user
    profile.setUserId(user.getId());

    Profile updatedProfile = profileDao.update(profile);
    return updatedProfile;
}

```

# 🧠 How This Works

### 1. Authentication Source
Spring Security injects a Principal object.
The username comes from the authenticated JWT/session

### 2.User Resolution
The username is used to retrieve the full User record. 
This provides access to the user’s database ID

### 3.Security Enforcement
The userId on the profile is explicitly set server-side. 
Any client-supplied userId is ignored or overwritten

### 4.Database Update
The DAO layer performs the update. 
The controller remains free of SQL logic
---

## 🎨 User Interface & Experience

The frontend UI was designed with a **modern, professional retail aesthetic**:

* Dark theme with accent colors
* Clear visual hierarchy
* Easy-to-navigate product grid
* Cart indicator always visible in the header

Design choices were made intentionally to improve clarity, usability, and visual appeal.

---

## 🧪 Testing & Stability

* Endpoints tested using Postman
* Input validation prevents crashes
* Application compiles and runs without errors
* Handles normal user flows reliably

---

---

## 🚀 Summary

EasyShop is a complete, secure, and scalable e-commerce application that demonstrates:

* Strong Java and Spring Boot fundamentals
* Real-world backend architecture
* Secure user profile handling
* Clean UI and professional documentation


