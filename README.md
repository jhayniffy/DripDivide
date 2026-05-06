# DripDivide 💧

**A Stellar-powered expense splitting app for instant, borderless debt settlement without high bank fees.**

![DripDivide Banner](https://img.shields.io/badge/Stellar-Network-blue) ![License](https://img.shields.io/badge/License-MIT-green) ![Status](https://img.shields.io/badge/Status-Active%20Development-yellow)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage Examples](#usage-examples)
- [Key Code Snippets](#key-code-snippets)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

**DripDivide** is a Splitwise-style expense splitting application that leverages the **Stellar blockchain network** to settle group debts instantly and securely across international borders. Unlike traditional payment methods, DripDivide eliminates high bank fees, currency conversion delays, and intermediaries.

Whether you're splitting rent with roommates, dividing travel expenses with friends, or managing shared costs across countries, DripDivide makes it seamless and affordable.

### Key Benefits
- ⚡ **Instant Settlement**: Settle debts in seconds using Stellar's blockchain
- 🌍 **Borderless**: No geographic restrictions or complex international transfers
- 💰 **Low Fees**: Minimal transaction costs compared to traditional banking
- 🔒 **Secure**: Built on blockchain technology with cryptographic verification
- 👥 **Group Management**: Easy group creation and expense tracking
- 📱 **User-Friendly**: Intuitive interface for managing shared expenses

---

## ✨ Features

### Core Features
- **User Authentication**: Secure account creation and login
- **Group Creation**: Create groups for different expense-sharing scenarios
- **Expense Tracking**: Add and categorize expenses within groups
- **Automatic Calculations**: Smart debt calculation and settlement suggestions
- **Stellar Integration**: Direct wallet integration for instant payments
- **Transaction History**: Complete audit trail of all transactions
- **Multi-Currency Support**: Handle multiple currencies via Stellar anchors
- **Real-time Notifications**: Get updates on payment status

### Advanced Features
- Group expense reports and analytics
- Recurring expense templates
- Payment request functionality
- Expense splitting by percentage, items, or equal share
- Receipt image attachments and storage
- Friend lists and quick group formation

---

## 🏗️ Architecture

### System Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                     DripDivide System Architecture              │
├─────────────────────────────────────────────────────────────────┤
│                                                                   │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                    Frontend Layer                         │  │
│  │  ┌─────────────┐  ┌──────────────┐  ┌──────────────┐    │  │
│  │  │  React App  │  │  Mobile Web  │  │   State Mgmt │    │  │
│  │  │  (Web UI)   │  │  (Responsive)│  │   (Redux)    │    │  │
│  │  └─────────────┘  └──────────────┘  └──────────────┘    │  │
│  └────────────────┬───────────────────────────────────────┘  │
│                   │ REST API / WebSocket                       │
│                   ▼                                             │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                   Backend Layer                          │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │  │
│  │  │ API Server   │  │ Auth Service │  │ Payment Mgr  │   │  │
│  │  │ (Node.js)    │  │ (JWT)        │  │ (Controller) │   │  │
│  │  └──────────────┘  └──────────────┘  └──────────────┘   │  │
│  │                                                            │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │  │
│  │  │ Group Mgr    │  │ Expense Svc  │  │ Settlement   │   │  │
│  │  │ (CRUD)       │  │ (Logic)      │  │ Engine       │   │  │
│  │  └──────────────┘  └──────────────┘  └──────────────┘   │  │
│  └────────────────┬───────────────────────────────────────┘  │
│                   │ Stellar SDK                               │
│                   ▼                                             │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │            Stellar Integration Layer                     │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │  │
│  │  │ Wallet Mgmt  │  │ Transaction  │  │ Smart        │   │  │
│  │  │              │  │ Builder      │  │ Contracts    │   │  │
│  │  └──────────────┘  └──────────────┘  └──────────────┘   │  │
│  └────────────────┬───────────────────────────────────────┘  │
│                   │                                             │
│                   ▼                                             │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │         Blockchain & Database Layer                      │  │
│  │  ┌────────────────┐  ┌────────────────┐  ┌──────────┐   │  │
│  │  │ Stellar Network│  │  PostgreSQL    │  │ Redis    │   │  │
│  │  │ (Public/Test)  │  │  (Persistence) │  │ (Cache)  │   │  │
│  │  └────────────────┘  └────────────────┘  └──────────┘   │  │
│  └──────────────────────────────────────────────────────────┘  │
│                                                                   │
└─────────────────────────────────────────────────────────────────┘
```

### Data Flow Diagram

```
User Action (Split Expense)
        │
        ▼
┌──────────────────┐
│  Frontend Form   │ ──► Validate Input
└──────────────────┘
        │
        ▼
┌──────────────────┐
│  Backend API     │ ──► Process Expense
└──────────────────┘
        │
        ▼
┌──────────────────┐
│ Settlement Logic │ ──► Calculate Debts
└──────────────────┘
        │
        ▼
┌──────────────────┐
│ Stellar Handler  │ ──► Create Transactions
└──────────────────┘
        │
        ▼
┌──────────────────┐
│ Stellar Network  │ ──► Execute & Confirm
└──────────────────┘
        │
        ▼
┌──────────────────┐
│  Database Update │ ──► Store Transaction
└──────────────────┘
        │
        ▼
┌──────────────────┐
│ Notify Users     │ ──► Send Confirmation
└──────────────────┘
```

---

## 🛠️ Tech Stack

### Frontend
- **React** - UI library
- **TypeScript** - Type safety
- **Redux** - State management
- **Axios** - HTTP client
- **Tailwind CSS** - Styling
- **React Router** - Navigation

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **TypeScript** - Type safety
- **PostgreSQL** - Primary database
- **Redis** - Caching layer
- **JWT** - Authentication

### Blockchain
- **Stellar SDK** - Blockchain interaction
- **Soroban** - Smart contracts (Rust)
- **Testnet/Mainnet** - Network options

### DevOps & Tools
- **Docker** - Containerization
- **Jest** - Testing framework
- **Git** - Version control

---

## 📦 Installation

### Prerequisites
- Node.js (v16+)
- PostgreSQL (v13+)
- Redis (v6+)
- Git

### Setup Instructions

#### 1. Clone Repository
```bash
git clone https://github.com/yourusername/dripdivide.git
cd dripdivide
```

#### 2. Backend Setup
```bash
cd backend
npm install

# Create .env file
cp .env.example .env

# Configure environment variables
# DATABASE_URL=postgresql://user:password@localhost:5432/dripdivide
# STELLAR_NETWORK=testnet
# JWT_SECRET=your_secret_key

# Run migrations
npm run migrate

# Start server
npm run dev
```

#### 3. Frontend Setup
```bash
cd ../frontend
npm install

# Create .env file
cp .env.example .env

# Configure environment variables
# REACT_APP_API_URL=http://localhost:3001

# Start development server
npm start
```

#### 4. Smart Contract Setup
```bash
cd ../contract

# Install Rust and Soroban CLI
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo install soroban-cli

# Build contract
soroban contract build

# Deploy to Stellar Testnet
soroban contract deploy --network testnet
```

---

## 📁 Project Structure

```
dripdivide/
├── frontend/                    # React web application
│   ├── src/
│   │   ├── components/         # Reusable UI components
│   │   ├── pages/              # Page components
│   │   ├── services/           # API & Stellar services
│   │   ├── store/              # Redux store & slices
│   │   ├── utils/              # Helper functions
│   │   ├── styles/             # Global styles
│   │   └── App.tsx             # Main app component
│   ├── public/                 # Static assets
│   └── package.json
│
├── backend/                     # Node.js/Express API
│   ├── src/
│   │   ├── routes/             # API endpoints
│   │   ├── controllers/        # Request handlers
│   │   ├── services/           # Business logic
│   │   ├── models/             # Database models
│   │   ├── middleware/         # Authentication, logging
│   │   ├── stellar/            # Stellar integration
│   │   ├── utils/              # Helper functions
│   │   └── server.ts           # Entry point
│   ├── migrations/             # Database migrations
│   ├── tests/                  # Test suites
│   └── package.json
│
├── contract/                    # Soroban smart contracts
│   ├── src/
│   │   ├── lib.rs              # Main contract logic
│   │   └── settlement.rs       # Settlement logic
│   ├── Cargo.toml
│   └── tests/
│
├── docker-compose.yml          # Docker services configuration
├── .env.example                # Environment variables template
└── README.md                   # This file
```

---

## 💻 Usage Examples

### 1. Create a Group
```bash
curl -X POST http://localhost:3001/api/groups \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "name": "Vegas Trip 2026",
    "description": "Group vacation expenses",
    "members": ["user1", "user2", "user3"]
  }'
```

### 2. Add an Expense
```bash
curl -X POST http://localhost:3001/api/expenses \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "groupId": "group123",
    "description": "Hotel booking",
    "amount": 1200.00,
    "currency": "USD",
    "paidBy": "user1",
    "splitAmong": ["user1", "user2", "user3"],
    "splitType": "equal"
  }'
```

### 3. Settle Debts
```bash
curl -X POST http://localhost:3001/api/settlements \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "groupId": "group123",
    "fromUserId": "user2",
    "toUserId": "user1",
    "amount": 400.00,
    "currency": "USD"
  }'
```

---

## 🔑 Key Code Snippets

### Backend: Settlement Service
```typescript
// backend/src/services/SettlementService.ts
import { StellarSDK } from 'stellar-sdk';

export class SettlementService {
  private stellarServer: StellarSDK.Server;

  constructor() {
    this.stellarServer = new StellarSDK.Server(
      'https://horizon-testnet.stellar.org'
    );
  }

  async settleDebt(
    fromAddress: string,
    toAddress: string,
    amount: string,
    assetCode: string = 'USD'
  ): Promise<string> {
    try {
      const sourceAccount = await this.stellarServer.loadAccount(fromAddress);
      
      const transaction = new StellarSDK.TransactionBuilder(sourceAccount, {
        fee: StellarSDK.BASE_FEE,
        networkPassphrase: StellarSDK.Networks.TESTNET_NETWORK_PASSPHRASE,
      })
        .addOperation(
          StellarSDK.Operation.payment({
            destination: toAddress,
            asset: new StellarSDK.Asset(assetCode, 'GBUQWP3BOUZX34ULNQG23RQ6F4YUSXHTTNUUK5GXV7STIS6PAAH6F7PS'),
            amount: amount,
          })
        )
        .setDefaultTimeout(300)
        .build();

      // Sign transaction with private key
      const keypair = StellarSDK.Keypair.fromSecret(process.env.PRIVATE_KEY!);
      transaction.sign(keypair);

      // Submit to Stellar Network
      const result = await this.stellarServer.submitTransaction(transaction);
      return result.id;
    } catch (error) {
      console.error('Settlement failed:', error);
      throw error;
    }
  }
}
```

### Backend: Expense Controller
```typescript
// backend/src/controllers/ExpenseController.ts
import { Request, Response } from 'express';
import { ExpenseService } from '../services/ExpenseService';

export class ExpenseController {
  private expenseService = new ExpenseService();

  async addExpense(req: Request, res: Response) {
    try {
      const { groupId, description, amount, currency, paidBy, splitAmong, splitType } = req.body;

      const expense = await this.expenseService.createExpense({
        groupId,
        description,
        amount,
        currency,
        paidBy,
        splitAmong,
        splitType,
      });

      // Calculate debts automatically
      const debts = await this.expenseService.calculateDebts(groupId);

      res.status(201).json({
        success: true,
        expense,
        debts,
      });
    } catch (error) {
      res.status(500).json({ success: false, error: error.message });
    }
  }

  async getGroupDebts(req: Request, res: Response) {
    try {
      const { groupId } = req.params;
      const debts = await this.expenseService.calculateDebts(groupId);

      res.json({
        success: true,
        debts,
      });
    } catch (error) {
      res.status(500).json({ success: false, error: error.message });
    }
  }
}
```

### Frontend: Expense Split Component
```typescript
// frontend/src/components/ExpenseSplit.tsx
import React, { useState } from 'react';
import { useDispatch } from 'react-redux';
import { createExpense } from '../store/expenseSlice';
import axios from 'axios';

export const ExpenseSplit: React.FC<{ groupId: string }> = ({ groupId }) => {
  const [amount, setAmount] = useState('');
  const [description, setDescription] = useState('');
  const [splitType, setSplitType] = useState<'equal' | 'percentage' | 'items'>('equal');
  const dispatch = useDispatch();

  const handleSplit = async () => {
    try {
      const response = await axios.post('/api/expenses', {
        groupId,
        description,
        amount: parseFloat(amount),
        splitType,
        currency: 'USD',
      });

      dispatch(createExpense(response.data.expense));
      setAmount('');
      setDescription('');
    } catch (error) {
      console.error('Failed to create expense:', error);
    }
  };

  return (
    <div className="expense-form">
      <input
        type="text"
        placeholder="Description"
        value={description}
        onChange={(e) => setDescription(e.target.value)}
      />
      <input
        type="number"
        placeholder="Amount"
        value={amount}
        onChange={(e) => setAmount(e.target.value)}
      />
      <select value={splitType} onChange={(e) => setSplitType(e.target.value as any)}>
        <option value="equal">Equal Split</option>
        <option value="percentage">Percentage</option>
        <option value="items">By Items</option>
      </select>
      <button onClick={handleSplit}>Split Expense</button>
    </div>
  );
};
```

### Smart Contract: Settlement Logic (Soroban/Rust)
```rust
// contract/src/lib.rs
#![no_std]

use soroban_sdk::{contract, contractimpl, symbol_short, Env, Symbol, Val};

#[contract]
pub struct SettlementContract;

#[contractimpl]
impl SettlementContract {
    pub fn settle_debt(
        env: Env,
        from: String,
        to: String,
        amount: i128,
        token: String,
    ) -> bool {
        // Validate addresses
        if from.is_empty() || to.is_empty() {
            return false;
        }

        // Create payment operation
        // This would interact with Stellar's native operations
        env.storage()
            .instance()
            .set(&symbol_short!("debt"), &(from, to, amount));

        true
    }

    pub fn get_debt(env: Env, from: String, to: String) -> i128 {
        env.storage()
            .instance()
            .get::<(String, String), i128>(&(from, to))
            .unwrap_or(0)
    }
}
```

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Workflow
```bash
# Install dependencies
npm install

# Run tests
npm test

# Check code quality
npm run lint

# Format code
npm run format
```

---

## 📝 API Documentation

### Authentication
All endpoints require a JWT token in the `Authorization` header:
```
Authorization: Bearer YOUR_JWT_TOKEN
```

### Endpoints Overview
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/groups` - Create group
- `GET /api/groups/:id` - Get group details
- `POST /api/expenses` - Add expense
- `GET /api/expenses/:groupId` - List expenses
- `POST /api/settlements` - Settle debt via Stellar
- `GET /api/settlements/:id` - Get settlement status

---

## 🔐 Security Considerations

- ✅ All API endpoints are protected with JWT authentication
- ✅ Private keys stored securely in environment variables
- ✅ HTTPS enforced in production
- ✅ Input validation on all endpoints
- ✅ Rate limiting implemented
- ✅ SQL injection prevention via parameterized queries
- ✅ CORS properly configured

---

## 📞 Support & Community

- **Issues**: [GitHub Issues](https://github.com/yourusername/dripdivide/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/dripdivide/discussions)
- **Documentation**: [Full Docs](https://docs.dripdivide.io)

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Built with [Stellar SDK](https://developers.stellar.org)
- Inspired by [Splitwise](https://www.splitwise.com)
- Community contributions and feedback

---

**Happy splitting! 💧**

*Last updated: May 6, 2026*
