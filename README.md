# 🛍️ Demo Web Shop - UI Automation Framework

This is a UI test automation project built using **Selenium**, **Java**, and **TestNG** to test key user flows on the [Demo Web Shop](https://demowebshop.tricentis.com/) e-commerce platform.

---

## ✅ Tech Stack

- Java
- Selenium WebDriver
- TestNG
- WebDriverManager
- Maven
- Page Object Model (POM) Design Pattern

---

## 📁 Project Structure
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

## 🚀 Features Covered (UI)

- Login (valid & invalid credentials)
- Product search
- Filter products by category and price
- Add products to cart
- View cart and verify totals
- Simulate multi-step checkout
- Order confirmation
- Form field validations (email, address, etc.)

---

## 🧪 UI Test Cases (Selenium + Java + TestNG)

### 1. **Login Functionality**
| Test Case ID | Description | Expected Result |
|--------------|-------------|-----------------|
| TC_UI_01 | Login with valid credentials | Redirects to account page with "Log out" link |
| TC_UI_02 | Login with invalid credentials | Error message: "Login was unsuccessful" |
| TC_UI_03 | Login with empty fields | Validation error prompts required input |
| TC_UI_04 | Password field left blank | Validation prompts for password |
| TC_UI_05 | Invalid email format | Email format error shown |

---

### 2. **Product Search & Filtering**
| Test Case ID | Description | Expected Result |
|--------------|-------------|-----------------|
| TC_UI_06 | Search by product keyword | Matching products should be displayed |
| TC_UI_07 | Apply category filter | Only products from selected category shown |
| TC_UI_08 | Filter by price range | Only products within selected price range shown |
| TC_UI_09 | Combine search and filters | Products match all selected criteria |

---

### 3. **Shopping Cart**
| Test Case ID | Description | Expected Result |
|--------------|-------------|-----------------|
| TC_UI_10 | Add product to cart | Product added to cart, cart count updated |
| TC_UI_11 | Update quantity in cart | Total price updates correctly |
| TC_UI_12 | Remove item from cart | Product removed and total updated |
| TC_UI_13 | Add multiple items to cart | All items correctly listed with combined total |

---

### 4. **Checkout Process**
| Test Case ID | Description | Expected Result |
|--------------|-------------|-----------------|
| TC_UI_14 | Fill billing & shipping info | Proceeds to payment step |
| TC_UI_15 | Leave required fields blank | Validation error shown |
| TC_UI_16 | Select payment method | Proceeds to confirm order |
| TC_UI_17 | Confirm and place order | Redirects to confirmation page with order ID |

---

### 5. **Order Confirmation**
| Test Case ID | Description | Expected Result |
|--------------|-------------|-----------------|
| TC_UI_18 | Verify order summary | All order details correctly displayed |
| TC_UI_19 | Check order number | Unique order ID shown on confirmation page |

---

## 🧰 Prerequisites

- JDK 8 or higher
- Maven
- Chrome browser
- Eclipse or IntelliJ IDE

---

## ▶️ How to Run

1. Clone the repo
2. Run `mvn clean install`
3. Execute tests via `testng.xml` or directly from the IDE

---

## 📌 Notes

- Tests are designed using the Page Object Model (POM)
- WebDriverManager handles browser drivers
- Assertions used to validate page behavior and elements

---




