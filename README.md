# 🛒 AutoCart

**AutoCart** is a Python + Selenium automation script that runs a complete online shopping journey, from browsing products to placing an order, on the [TutorialsNinja demo store](http://tutorialsninja.com/demo/) without any manual clicking.

It is a hands-on example of end-to-end (E2E) web UI automation: navigation, hover menus, image galleries, date pickers, dropdowns, form filling, guest checkout, screenshots, and result verification.

---

## ✨ Features

- Opens the demo store and maximizes the browser window
- Navigates to **Phones & PDAs** and opens the **iPhone** product page
- Browses the product image gallery (opens the first image, clicks through next 5 times)
- Saves a **screenshot** of the gallery
- Sets quantity to 2 and adds the iPhone to the cart
- Uses **hover (ActionChains)** to open the Laptops menu and selects **HP LP3065**
- Scrolls to the *Add to Cart* button and selects a delivery date in the **calendar widget**
- Proceeds to checkout as a **guest**
- Fills the billing form (name, email, phone, address, city, postcode)
- Selects country and region from **dropdowns**
- Accepts terms & conditions and completes the checkout steps
- Prints the **final order price** and the **order success message**

---

## 🧰 Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Scripting language |
| Selenium WebDriver | Browser automation |
| ChromeDriver | Controls Google Chrome |

---

## 📁 Project Structure

```
AutoCart/
├── main.py          # Main automation script
└── README.md
```

> Rename `main.py` to match your actual file name.

---

## ⚙️ Prerequisites

- Python 3.7+
- Google Chrome installed
- [ChromeDriver](https://chromedriver.chromium.org/downloads) matching your Chrome version
- Selenium 3.x (see the compatibility note below)

---

## 🚀 Setup & Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/AutoCart.git
   cd AutoCart
   ```

2. **Install Selenium**
   ```bash
   pip install "selenium<4.3"
   ```

3. **Set the ChromeDriver path** in the script:
   ```python
   driver = webdriver.Chrome('C:/bin/chromedriver3.exe')
   ```
   Change the path to wherever your `chromedriver` lives.

4. **Run the script**
   ```bash
   python main.py
   ```

---

## 📸 Sample Output

```
The final price of both products is $1,xxx.xx
Your order has been placed!
```

A screenshot named `screenshot#<number>.png` is saved in the project folder.

---

## 🔄 Automation Flow

```
Home → Phones & PDAs → iPhone → Gallery → Screenshot → Qty 2 → Add to Cart
     → Laptops (hover) → HP LP3065 → Pick date → Add to Cart
     → Cart → Checkout → Guest → Billing details → Shipping → Terms
     → Payment → Confirm order → Success message
```

---

## ⚠️ Compatibility Notes

- The script uses `find_element_by_*` methods, which were **removed in Selenium 4.3+**. Either install an older version (`selenium<4.3`) or update the calls to the new syntax:
  ```python
  from selenium.webdriver.common.by import By
  driver.find_element(By.XPATH, '//a[text()="Phones & PDAs"]')
  ```
- The calendar step targets **December 2022**. Since that date has passed, change the target month or the date picker will not stop at the right place.
- The demo site is public and may change its layout, so locators can break over time.

---

## 🔮 Future Improvements

- Replace `time.sleep()` with Selenium **explicit waits** (`WebDriverWait`)
- Migrate to **Selenium 4** syntax and use Selenium Manager (no manual ChromeDriver path)
- Adopt the **Page Object Model** for cleaner, reusable code
- Add **pytest** test cases with assertions and HTML reports
- Add headless mode and cross-browser support (Firefox, Edge)
- Move test data (name, address, etc.) into a config file
