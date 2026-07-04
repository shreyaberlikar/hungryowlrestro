# Smart Restaurant POS

A full desktop Restaurant Billing System built with **JavaFX**, **SQLite**, and **Apache PDFBox**.

Features: Table management, Order taking, Billing (tax/discount), Inventory with low-stock alerts, Sales Analytics (charts), and PDF Invoice generation.

---

## Running in VS Code

### 1. Install prerequisites
- **JDK 17 or later** — https://adoptium.net/
- **Apache Maven** — https://maven.apache.org/download.cgi (make sure `mvn` works in a terminal)
- **VS Code extensions:**
  - "Extension Pack for Java" (Microsoft) — installs Java language support + Maven for Java + Debugger
  - That's it — no separate JavaFX extension is needed since we use the `javafx-maven-plugin`.

### 2. Open the project
Open this folder (`smart-restaurant-pos`) in VS Code: **File → Open Folder**.

Wait a few seconds for the Java extension to detect the Maven project (watch the bottom status bar / "Java Projects" view in the sidebar).

### 3. Run it
Open a terminal in VS Code (`` Ctrl+` ``) and run:

```bash
mvn clean javafx:run
```

The first run downloads dependencies (JavaFX, SQLite JDBC, PDFBox) — that's normal and only happens once.

A window titled **"Smart Restaurant POS"** should open. A `restaurant.db` SQLite file is created automatically in the project folder on first launch, pre-seeded with sample menu items, tables, and inventory so the app looks populated right away.

### Alternative: run via the Maven sidebar
If you don't want to use the terminal, the Java extension adds a **Maven** view in the sidebar (Explorer). Expand `smart-restaurant-pos → Plugins → javafx → javafx:run` and double-click it.

---

## Project Structure

```
smart-restaurant-pos/
├── pom.xml
├── src/main/java/com/restaurant/pos/
│   ├── Main.java                 # app entry point
│   ├── db/DatabaseManager.java   # SQLite connection + schema + seed data
│   ├── model/                    # MenuItem, RestaurantTable, Order, OrderItem, Bill, InventoryItem
│   ├── dao/                      # JDBC data access objects (one per table)
│   ├── service/                  # OrderService, BillingService, InvoiceService (PDF)
│   └── controller/                # JavaFX controllers, one per screen
└── src/main/resources/com/restaurant/pos/
    ├── fxml/                     # Screen layouts (dashboard, menu, tables, orders, billing, inventory, analytics)
    └── css/style.css             # App styling
```

## How to Use It

1. **Tables** — add tables, click a free/reserved table tile to toggle its status.
2. **Orders** — pick a table from the dropdown (auto-creates an order + marks table occupied), add menu items with quantities, then **Generate Bill**.
3. **Billing** — see all bills, **Mark Paid** (frees the table) or **Print Invoice (PDF)** to save a formatted invoice.
4. **Menu** — add/remove menu items and categories.
5. **Inventory** — track stock; rows highlighted red are at/below their reorder level; use **Restock Selected** to add quantity.
6. **Analytics** — revenue today/total, 7-day revenue bar chart, and a pie chart of top-selling items (populates as you generate paid bills).

## Notes / Possible Extensions

- Tax rate is currently a flat 5%, set in `BillingService.TAX_RATE`.
- To reset all data, just delete `restaurant.db` and restart — it'll be recreated and reseeded.
- Ideas to extend further for your resume project: login/roles (admin vs waiter), kitchen order tickets (KOT) printing, item-level inventory deduction on order, monthly analytics view, dark mode toggle.
