#  Demo Web Shop - UI Automation Framework

This is a UI test automation project built using **Selenium**, **Java**, and **TestNG** to test key user flows on the [Demo Web Shop](https://demowebshop.tricentis.com/) e-commerce platform.

---

##  Tech Stack

- Java
- Selenium WebDriver
- TestNG
- WebDriverManager
- Maven
- Page Object Model (POM) Design Pattern

---

##  Project Structure
DemoWebShopAutomation/
- ├── src/
- │ ├── base/ # WebDriver setup, base classes
- │ ├── pages/ # Page Object Model classes
- │ ├── tests/
- │ │ └── ui/ # UI test classes
- ├── pom.xml # Maven dependencies
- ├── testng.xml # TestNG suite config
- └── README.md # Project documentation

---

---

##  Features Covered (UI)

- Login (valid & invalid credentials)
- Product search
- Filter products by category and price
- Add products to cart
- View cart and verify totals
- Simulate multi-step checkout
- Order confirmation
- Form field validations (email, address, etc.)

---
#                   Begginer 
##  UI Test Cases (Selenium + Java + TestNG)

### 1. **Login Functionality**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_UI_01 | Login with valid credentials | Enter valid email and password → Click "Login" |Redirects to account page with "Log out" link |
| TC_UI_02 | Login with invalid password |Enter valid email, incorrect password → Click "Login" | Error message displayed: "Login was unsuccessful. Please correct the errors and try again."" |
| TC_UI_03 | Login with unregistered email | Enter an email not in system → Enter any password → Click "Login" | Same error as above, login not allowed |
| TC_UI_04 | Login with empty fields | Leave email and password fields blank → Click "Login" | Validation message: "Email is required", "Password is required" |
| TC_UI_05 | 	Login with empty password | Enter email → Leave password blank → Click "Login" | Validation message: "Password is required" |
| TC_UI_06 | Login with invalid email format | Enter malformed email (e.g., user@) → Click "Login" | Error message: "Wrong email" or HTML5 input validation or email format error |
| TC_UI_07 | Login, then logout | Login successfully → Click “Log out” | Redirects to home page with “Log in” link shown again |
| TC_UI_08 | “Remember Me” checkbox functionality | Check "Remember Me" → Login → Close and reopen browser | User remains logged in (if site supports session persistence)|
| TC_UI_09 | 	Session timeout after inactivity | Login → Wait for session timeout period → Try any action | User should be redirected to login page (if implemented) |

---

### 2. **Product Search & Filtering**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_UI_10 | Search by product keyword | Enter "laptop" in the search bar → Click Search | Matching products containing "laptop" in name or description are listed |
| TC_UI_11 | Apply category filter | 	Navigate to "Books" category → View listed products | Only products from selected category shown |
| TC_UI_12 | Filter by price range | Select price range filter (e.g., $50 - $100) | Only products within selected price range shown |
| TC_UI_13 | Combine search and filters | Search for “phone” → Apply category “Electronics” → Set price filter | Products matching all combined criteria are displayed |
| TC_UI_14 | Search invalid keyword | Enter random term “xyz123” in search bar → Click Search | Message displayed: "No products were found that matched your criteria." |

---

### 3. **Shopping Cart**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_UI_15 | Add product to cart | On product page, click "Add to Cart" | Product added to cart, cart count updated OR Confirmation message shown, cart item count increases |
| TC_UI_16 | Update quantity in cart | Go to cart → Change quantity of an item → Click “Update” | Total price updates correctly  OR Total price recalculates based on new quantity |
| TC_UI_17 | Remove item from cart | Click "Remove" next to a product in the cart | Product removed and total updated correctly |
| TC_UI_18 | Add multiple items to cart | Add 3 different items → View cart | All products appear with individual and total pricing |
| TC_UI_19 | Empty cart and validate | Remove all items → Check cart status | Message shown: "Your Shopping Cart is empty." |

---

### 4. **Checkout Process**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_UI_20 | Fill billing & shipping info | Proceed to checkout → Enter valid details | Navigates to payment method step |
| TC_UI_21 | Leave required fields blank | Proceed without entering address/email | Validation error shown: "This field is required." |
| TC_UI_22 | Select payment method | Choose "Credit Card" or "Cash on Delivery" | Proceeds to confirm order OR Navigates to confirm order step |
| TC_UI_23 | Confirm and place order | Review details → Click "Confirm" | Redirected to order confirmation page with order number |
| TC_UI_24 | Simulate invalid form inputs | Enter invalid ZIP code or characters in address | Appropriate field-level error messages shown |

---

### 5. **Order Confirmation**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_UI_25 | Verify order summary | Complete order → Review confirmation page | All order details correctly displayed -Products, price, tax, shipping, and total all shown correctly |
| TC_UI_26 | Check order number | Complete order → View confirmation screen | Unique order ID shown on confirmation page |
| TC_UI_27 | View/download invoice (if available) | Click "Print invoice" or similar | 	Invoice view opens or PDF downloads successfully |
| TC_UI_28 | Navigate back to home after order | Click “Continue” or “Home” after placing order | Redirects user to home or dashboard page |

---

##  API Test Cases

### 1. **Login API**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_API_01 | Login with valid credentials | Send POST request to /login with valid email & password | Response code 200, token or success message returned |
| TC_API_02 | Login with invalid credentials | Send POST request with wrong email/password | Response code 401, error message "Invalid credentials" |
| TC_API_03 | Login with missing fields | Send POST request with missing password/email | Response code 400, validation error message |

---

### 2. **Product API**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_API_04 | Get all products | Send GET request to /products | Response 200, list of all products with details |
| TC_API_05 | Get product by ID | Send GET request to /products/{id} | Response 200 with correct product data |
| TC_API_06 | Get non-existent product | Send GET request to /products/invalid-id | Response 404 with message "Product not found" |

---

### 3. **Cart API**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_API_07 | Add item to cart | Send POST request to /cart/add with product ID and quantity | Response 200, item added confirmation |
| TC_API_08 | View cart | Send GET request to /cart | Response 200 with list of items in cart |
| TC_API_09 | Remove item from cart | Send DELETE request to /cart/remove/{productId} | Response 200, confirmation of removal |
| TC_API_10 | Empty cart | Send DELETE request to /cart/clear | Response 200, empty cart confirmation |

---

### 4. **Order API**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_API_11 | Place a new order | Send POST request to /orders with cart and billing info | Response 201, new order ID returned |
| TC_API_12 | Get order by ID | Send GET request to /orders/{orderId} | Response 200, full order details returned |
| TC_API_13 | Invalid order submission | Send POST to /orders with missing fields | Response 400, validation errors |

---

### 5. **Error Handling & Security**
| Test Case ID | Description | Steps | Expected Result |
|--------------|-------------|-----------------|-----------------|
| TC_API_14 | Access protected route unauthenticated | Send GET to /orders without token | Response 401 Unauthorized |
| TC_API_15 | Invalid method | Send PUT to /cart where only GET/POST allowed | Response 405 Method Not Allowed |

---
# Intermediate Test Cases
## UI Testing 
## API Nothing 
---
##  Prerequisites

- JDK 8 or higher
- Maven
- Chrome browser
- Eclipse or IntelliJ IDE

---

## ▶ How to Run

1. Clone the repo
2. Run `mvn clean install`
3. Execute tests via `testng.xml` or directly from the IDE

---

##  Notes

- Tests are designed using the Page Object Model (POM)
- WebDriverManager handles browser drivers
- Assertions used to validate page behavior and elements

---




