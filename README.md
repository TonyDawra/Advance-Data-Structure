# Chart of Accounts Management

A console-based C++ application to manage a hierarchical chart of accounts, supporting account creation/deletion, transaction processing, balance aggregation, and report generation. Data is stored in a forest of account-nodes, where each node can have subaccounts and transactions.

---

## Features

* **Create** an empty chart (forest) of accounts
* **Load** predefined accounts from a file into the forest
* **Add** or **delete** accounts at any level (subaccounts determined by account number prefixes)
* **Record** debit/credit transactions on any account; auto-incrementing transaction IDs
* **Remove** transactions and automatically revert balances
* **Aggregate** balances up the tree so parent accounts reflect sums of their children
* **Print** the chart in an indented, human-readable format
* **Save** the entire chart or generate detailed per-account report files

---

## Prerequisites

* C++17 (or later) compiler
* CMake (optional) or manual compilation via `g++`/`clang++`
* Standard library support for `<filesystem>`, `<vector>`, `<string>`

---

## Project Structure

```
.
├── Account.h/.cpp         # Account class: ID, description, balance, transaction list
├── Transaction.h/.cpp     # Transaction class: auto IDs, amount, type, I/O operators
├── ForestTree.h/.cpp      # ForestTree class: hierarchical insert/delete, balance updates, print/save/report
├── main.cpp               # CLI entry point: menu, file loading, user interaction
└── accounts.txt           # Sample input file: each line `<acct#> "Description" <balance>`  
```

---

## Data File Format

Each non-empty, non-comment line in `accounts.txt` must follow:

```
<accountNumber> "<description>" <balance>
```

* **accountNumber**: integer; subaccounts share prefix (e.g. 12 → children 123, 124)
* **description**: quoted string
* **balance**: initial balance (double)

Lines beginning with `#` or blank lines are ignored.

---

## Build & Run

### Manual (g++)

```bash
g++ -std=c++17 Account.cpp Transaction.cpp ForestTree.cpp main.cpp -o chart_of_accounts
./chart_of_accounts
```

### CMake (if desired)

```bash
mkdir build && cd build
cmake ..
make
./chart_of_accounts
```

---

## Usage

Upon launch, choose from the menu:

```
1.  Create Empty Forest
2.  Add an Account
3.  Delete an Account
4.  Add a Transaction for an Account
5.  Delete a Transaction for an Account
6.  Find an Account
7.  Generate Detailed Account File
8.  Print Account Charts
9.  Save Account Charts
10. Load Predefined Account Charts Data
11. Load from Saved File
12. Exit
```

* **Add Account**: specify account number, description, starting balance
* **Transactions**: enter amount and type (`D` for debit, `C` for credit)
* **Generate Detailed File**: creates a formatted report under `accounts/` for a given account and its subaccounts

---

## Extending & Contributing

1. Fork the repository.
2. Create a feature branch:

   ```bash
   git checkout -b feature/YourFeature
   ```
3. Commit changes with descriptive messages.
4. Submit a pull request for review.

---

## License

This project is provided under the MIT License. See `LICENSE` for details.
