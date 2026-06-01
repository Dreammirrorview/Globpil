# Global Pilgrim Bank Nigeria — Login Credentials & System Guide

---

## 🔐 ADMIN LOGIN DETAILS

| Field       | Value              |
|-------------|--------------------|
| Username    | `olawale`          |
| Password    | `pilgrimolawale`   |

Admin has full access to: Dashboard Overview, Customer Management, Create Customers, View All Transactions, Ledger Entries, SMS/Email Alerts, Credit/Debit Accounts, Flow Verification, System Settings.

---

## 👤 CUSTOMER LOGIN DETAILS

Customers log in using their **Account Number** and **4–6 digit PIN**.

### Customer 1 — OWNER ACCOUNT
| Field            | Value                              |
|------------------|------------------------------------|
| Account Number   | `2345921499`                       |
| PIN              | `123456`                           |
| Full Name        | Olawale Abdul-ganiyu Adeshina      |
| Email            | olawale@globalpilgrimbabwe.com.ng  |
| Phone            | +234-801-234-5678                  |
| Balance          | ₦1,000,000,000.00                  |
| Currency         | NGN                                |

### Customer 2
| Field            | Value                              |
|------------------|------------------------------------|
| Account Number   | `1234567890`                       |
| PIN              | `654321`                           |
| Full Name        | Adebayo Chukwuma                   |
| Email            | adebayo@example.com                |
| Phone            | +234-802-345-6789                  |
| Balance          | ₦500,000.00                        |
| Currency         | NGN                                |

### Customer 3
| Field            | Value                              |
|------------------|------------------------------------|
| Account Number   | `9876543210`                       |
| PIN              | `112233`                           |
| Full Name        | Fatima Ibrahim                     |
| Email            | fatima@example.com                 |
| Phone            | +234-803-456-7890                  |
| Balance          | ₦750,000.00                        |
| Currency         | NGN                                |

### Customer 4
| Field            | Value                              |
|------------------|------------------------------------|
| Account Number   | `5555666677`                       |
| PIN              | `445566`                           |
| Full Name        | Emeka Okafor                       |
| Email            | emeka@example.com                  |
| Phone            | +234-804-567-8901                  |
| Balance          | ₦2,500,000.00                      |
| Currency         | NGN                                |

### Customer 5
| Field            | Value                              |
|------------------|------------------------------------|
| Account Number   | `1111222233`                       |
| PIN              | `778899`                           |
| Full Name        | Aisha Bello                        |
| Email            | aisha@example.com                  |
| Phone            | +234-805-678-9012                  |
| Balance          | ₦10,000,000.00                     |
| Currency         | NGN                                |

---

## 🔄 TRANSACTION FLOW (Verified & Working)

Every transfer goes through **4 sequential steps**. If any step fails, the transaction is rolled back.

1. **Wallet Debit** — Sender's wallet is debited the transfer amount
2. **Payment API** — Funds are sent to the recipient's account (internal or external bank)
3. **Ledger Update** — Double-entry ledger records are created (debit for sender, credit for recipient)
4. **SMS/Email Alert** — Both sender and recipient receive notification alerts

### Verification Endpoint
Send a GET request to: `/api/verify-flow`

This checks that all 4 components (Wallet Debit, Payment API, Ledger Update, Alert Generation) are operational.

---

## 🏦 BANK INFORMATION

| Field          | Value                              |
|----------------|------------------------------------|
| Bank Name      | Global Pilgrim Bank Nigeria        |
| Bank Code      | 999                                |
| SWIFT Code     | GPBINGLA                           |
| NIBSS Code     | 999001                             |
| CBN License    | CBN/BNK/2024/999                   |
| Owner          | Olawale Abdul-ganiyu Adeshina      |
| Owner BVN      | 22203477535                        |
| Owner NIN      | 87142812384                        |

---

## 📡 API ENDPOINTS

### Admin Endpoints
- `POST /api/admin/login` — Admin authentication
- `GET /api/admin/overview` — Dashboard statistics
- `GET /api/admin/customers` — List all customers
- `POST /api/admin/customers` — Create new customer
- `GET /api/admin/transactions` — All transactions
- `GET /api/admin/ledger` — Ledger entries
- `GET /api/admin/alerts` — All SMS/Email alerts
- `POST /api/admin/credit` — Credit a customer account
- `POST /api/admin/debit` — Debit a customer account

### Customer Endpoints
- `POST /api/customer/login` — Customer authentication (account number + PIN)
- `GET /api/customer/:account` — Customer details
- `GET /api/customer/:account/transactions` — Customer transactions
- `GET /api/customer/:account/ledger` — Customer ledger
- `GET /api/customer/:account/alerts` — Customer alerts

### Transaction Endpoints
- `POST /api/transfer` — Execute full transfer (debit → payment → ledger → alert)
- `GET /api/verify-flow` — Verify all 4 transaction steps are operational
- `GET /api/lookup/:accountNumber` — Look up account holder name

### System Endpoints
- `GET /api/system/info` — Bank & system information

---

## 🚀 HOW TO RUN

### Backend
```bash
cd pilgrim-bank/backend
npm install
node server.js
# Server runs on http://localhost:3001
```

### Frontend
Open `pilgrim-bank/frontend/index.html` in any browser, or serve it:
```bash
cd pilgrim-bank/frontend
npx serve .
# Or use any HTTP server
```

The frontend is configured to connect to the backend at `http://localhost:3001` by default.

---

## 📁 PROJECT STRUCTURE

```
pilgrim-bank/
├── CREDENTIALS.md          ← This file
├── backend/
│   ├── server.js           ← Express API server
│   ├── package.json        ← Node.js dependencies
│   └── node_modules/       ← Installed packages
└── frontend/
    ├── index.html          ← Full banking application UI
    └── owner-photo.jpg     ← Bank owner photograph
```

---

*Global Pilgrim Bank Nigeria — Built with ❤️ for Nigeria*
