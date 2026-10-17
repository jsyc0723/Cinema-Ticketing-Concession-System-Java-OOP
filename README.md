# 🎬 Cinema Ticketing & Concession System

A console-based Java application built as a group assignment for **AMCS2204 Object-Oriented Programming Techniques** at TAR UMT. The system simulates a multiplex cinema management platform covering user management, movie browsing, seat selection, food ordering, reward redemption, payment processing, and staff reporting.

---

## 📌 Features

### Customer
- Register and log in with credential validation
- Browse cinemas, movies, and showtimes with keyword filtering
- Select seats via an interactive 2D seat map
- Choose ticket types (Adult / Child / Senior) per seat
- Order snacks, drinks, and combos from a concession menu
- Apply reward codes for discounts or freebies at checkout
- Pay via Credit Card or E-Wallet with full input validation

### Staff
- Log in and manage personal profile
- View all registered customers and staff
- Manage movies, cinemas, halls, shows, and rewards (CRUD)
- Validate tickets at the entrance
- Generate reports: customer summary, staff summary, booking summary, peak hours, top reward points, system overview

---

## 🗂️ Project Structure

```
├── CinemaDriver.java       # Main entry point — connects all modules
├── User.java               # Abstract base class (abstraction)
├── Customer.java           # Extends User — customer portal
├── Staff.java              # Extends User — staff portal
├── DataStorage.java        # File-based CRUD persistence (users.txt, bookings.txt)
├── Report.java             # Report generation module
├── Movie.java              # Movie management with file I/O (movies.txt)
├── Show.java               # Show scheduling linked to Movie, Cinema, Hall
├── Cinema.java             # Cinema entity with hall management
├── Hall.java               # Hall management with file I/O (halls.txt)
├── Seat.java               # 2D seat map for Small / Medium / Large halls
├── Booking.java            # Booking entity linking Show, FoodOrder, Tickets
├── Ticket.java             # Ticket types and pricing
├── FoodOrder.java          # Base food order class
├── Snack.java              # Extends FoodOrder — snack menu
├── Drink.java              # Extends FoodOrder — drink menu
├── Combo.java              # Extends FoodOrder — combo menu
├── Payment.java            # Payment calculation with tax and discount
├── PaymentMethod.java      # Abstract payment method base class
├── CreditCardPayment.java  # Extends PaymentMethod — credit card flow
├── EWalletPayment.java     # Extends PaymentMethod — e-wallet flow
├── Reward.java             # Abstract reward base class
├── Discount.java           # Extends Reward — percentage discount
├── Freebie.java            # Extends Reward — freebie items
├── Redemption.java         # Reward redemption tracking
└── Utils.java              # Shared utility methods (screen clear, input range)
```

---

## 🧠 OOP Concepts Applied

| Concept | Where Applied |
|---|---|
| **Abstraction** | `User` (abstract), `Reward` (abstract), `PaymentMethod` (abstract), `FoodOrder` (abstract) |
| **Inheritance** | `Customer`, `Staff` extend `User`; `Snack`, `Drink`, `Combo` extend `FoodOrder`; `Discount`, `Freebie` extend `Reward`; `CreditCardPayment`, `EWalletPayment` extend `PaymentMethod` |
| **Encapsulation** | All fields private across every class; accessed via getters and setters only |
| **Polymorphism** | `toString()` and `equals()` overridden in all classes; runtime dispatch via `User` reference in driver |
| **Aggregation** | `DataStorage` aggregates `List<Customer>`, `List<Staff>`, `List<Booking>` |
| **Dependency** | `Report` depends on `DataStorage` via method parameter |
| **Composition** | `Booking` composed of `Show`, `FoodOrder`, `Ticket[]` |

---

## 💾 Data Persistence

All data is saved to plain `.txt` files using `BufferedReader` and `BufferedWriter`:

| File | Contents |
|---|---|
| `data/users.txt` | Registered customers and staff with hashed-style records |
| `data/bookings.txt` | Booking records: customer, movie, show, hall, tickets, food, payment |
| `movies.txt` | Movie catalogue managed by `Movie.java` |
| `halls.txt` | Hall records managed by `Hall.java` |
| `seats_data.txt` | Seat booking status for all hall types |
| `orders.txt` | Food order records |

---

## ▶️ How to Run

**Requirements:** Java JDK 11 or above

```bash
# Compile all files
javac *.java

# Run the program
java CinemaDriver
```

> All `.txt` data files are created automatically on first run inside a `data/` folder.

---

## 👥 Team Contributions

| Member | Module |
|---|---|
| James | User Management (`User`, `Customer`, `Staff`), `DataStorage`, `Report`, Main Driver |
| Member 2 | Movie, Show, Cinema, Hall management |
| Member 3 | Booking, Ticket, Seat selection flow |
| Member 4 | Food Order (Snack, Drink, Combo), Payment, Reward, Redemption |

---

## 📚 Course

**AMCS2204 Object-Oriented Programming Techniques**  
TAR UMT — Group Assignment
