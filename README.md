# 🍽️ Smart Restaurant POS

> **A desktop-based Restaurant Billing & Management System built using JavaFX, SQLite, and Apache PDFBox for efficient restaurant operations.**

---

## 📖 Overview

Smart Restaurant POS is a comprehensive desktop application designed to simplify restaurant management. It enables restaurants to manage tables, process customer orders, generate bills, monitor inventory, analyze sales, and create professional PDF invoices—all within an intuitive JavaFX interface.

---

## ✨ Features

- 🍽️ Table Management
- 📝 Order Taking & Management
- 💳 Billing with Tax & Discount Calculation
- 📦 Inventory Management with Low-Stock Alerts
- 📊 Sales Analytics & Charts
- 📄 PDF Invoice Generation
- 💻 User-friendly JavaFX Interface

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|--------------|
| **Programming Language** | Java |
| **Framework** | JavaFX |
| **Database** | SQLite |
| **PDF Generation** | Apache PDFBox |
| **Build Tool** | Maven |
| **IDE** | VS Code |

---

# 🚀 Running in VS Code

## 1️⃣ Install Prerequisites

- **JDK 17 or later** — https://adoptium.net/
- **Apache Maven** — https://maven.apache.org/download.cgi *(make sure `mvn` works in a terminal)*

### VS Code Extensions

- **Extension Pack for Java (Microsoft)**
  - Java Language Support
  - Maven for Java
  - Java Debugger

> No separate JavaFX extension is required since the project uses the `javafx-maven-plugin`.

---

## 2️⃣ Open the Project

Open the **smart-restaurant-pos** folder in VS Code.

```
File → Open Folder
```

Wait a few seconds for the Java extension to detect the Maven project. You can verify this in:

- Java Projects
- Maven View
- Status Bar

---

## 3️⃣ Run the Application

Open the VS Code terminal:

```bash
mvn clean javafx:run
```

During the first run, Maven automatically downloads:

- JavaFX
- SQLite JDBC
- Apache PDFBox

A window titled **Smart Restaurant POS** will open.

On the first launch, a **restaurant.db** SQLite database is automatically created and pre-populated with:

- Sample Menu Items
- Restaurant Tables
- Inventory Records

---

## ▶️ Alternative: Run Using Maven Sidebar

Instead of using the terminal:

```
Explorer
   └── Maven
       └── smart-restaurant-pos
            └── Plugins
                 └── javafx
                      └── javafx:run
```

Double-click **javafx:run**.

---

# 📂 Project Structure

```text
smart-restaurant-pos/
├── pom.xml
├── src/main/java/com/restaurant/pos/
│   ├── Main.java                 # app entry point
│   ├── db/DatabaseManager.java   # SQLite connection + schema + seed data
│   ├── model/                    # MenuItem, RestaurantTable, Order, OrderItem, Bill, InventoryItem
│   ├── dao/                      # JDBC data access objects (one per table)
│   ├── service/                  # OrderService, BillingService, InvoiceService (PDF)
│   └── controller/               # JavaFX controllers, one per screen
└── src/main/resources/com/restaurant/pos/
    ├── fxml/                     # Screen layouts (dashboard, menu, tables, orders, billing, inventory, analytics)
    └── css/style.css             # Application styling
```

---

# 📖 How to Use It

### 🍽️ Tables

- Add new tables.
- Click a table tile to toggle between **Free** and **Reserved** status.

---

### 📝 Orders

- Select a table from the dropdown.
- An order is automatically created.
- Add menu items with quantities.
- Click **Generate Bill**.

---

### 💳 Billing

- View generated bills.
- Mark bills as **Paid**.
- Automatically free occupied tables.
- Generate professional **PDF invoices**.

---

### 🍔 Menu

- Add menu items.
- Remove menu items.
- Manage food categories.

---

### 📦 Inventory

- Monitor stock availability.
- Low-stock items are highlighted in **red**.
- Restock inventory using **Restock Selected**.

---

### 📊 Analytics

Track restaurant performance through:

- Today's Revenue
- Total Revenue
- 7-Day Revenue Bar Chart
- Top-Selling Items Pie Chart

Charts update automatically as paid bills are generated.

---

# 🔮 Notes / Possible Extensions

- Tax rate is currently **5%**, configurable in:

```java
BillingService.TAX_RATE
```

- To reset the application data:

Delete the database file:

```
restaurant.db
```

Restart the application and it will automatically recreate and reseed the database.

### Future Improvements

- 👤 User Authentication (Admin / Waiter)
- 🍳 Kitchen Order Ticket (KOT) Printing
- 📦 Automatic Inventory Deduction
- 📅 Monthly Sales Analytics
- 🌙 Dark Mode Support

---

## 👩‍💻 Author

**Shreya Berlikar**

- GitHub: https://github.com/shreyaberlikar
- LinkedIn: https://linkedin.com/in/shreya-berlikar

---

## 📄 License

This project is developed for **educational and learning purposes**.

---

⭐ If you found this project useful, consider giving it a **Star** on GitHub!
