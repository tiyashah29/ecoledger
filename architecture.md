# Carbon Credit Tracking System - Architecture Plan

## Overview
A blockchain-based Carbon Credit Tracking System that records carbon emissions and credits with transparency and immutability. The app features a sleek, modern UI with custom design (non-Material Design aesthetics).

## Technical Stack
- **Frontend**: Flutter with custom modern UI design
- **Blockchain**: Web3 integration using web3dart package
- **Local Storage**: shared_preferences for local data persistence
- **State Management**: Built-in Flutter state management (StatefulWidget)
- **HTTP Client**: http package for blockchain API calls

## Core Features (MVP)
1. **Dashboard**: Overview of total carbon credits, emissions, and blockchain transactions
2. **Record Emissions**: Log carbon emission activities with details
3. **Record Credits**: Log carbon credit generation/purchase
4. **Blockchain Transactions**: View all blockchain-recorded transactions with hash verification
5. **Transaction Details**: View individual transaction details with blockchain proof
6. **Statistics**: Visual representation of carbon footprint over time

## Data Models (lib/models)

### 1. User Model (`user_model.dart`)
- `id` (String)
- `name` (String)
- `email` (String)
- `walletAddress` (String) - blockchain wallet
- `totalEmissions` (double) - in tons CO2
- `totalCredits` (double) - in credits
- `created_at` (DateTime)
- `updated_at` (DateTime)

### 2. Transaction Model (`transaction_model.dart`)
- `id` (String)
- `userId` (String)
- `type` (enum: emission/credit)
- `amount` (double)
- `category` (String) - e.g., "Transportation", "Energy", "Renewable"
- `description` (String)
- `blockchainHash` (String) - transaction hash on blockchain
- `blockNumber` (int)
- `timestamp` (DateTime)
- `status` (enum: pending/confirmed/failed)
- `created_at` (DateTime)
- `updated_at` (DateTime)

### 3. BlockchainRecord Model (`blockchain_record_model.dart`)
- `transactionHash` (String)
- `blockNumber` (int)
- `fromAddress` (String)
- `toAddress` (String)
- `amount` (double)
- `gasUsed` (int)
- `timestamp` (DateTime)
- `confirmations` (int)

## Service Classes (lib/services)

### 1. User Service (`user_service.dart`)
- `Future<User> getCurrentUser()` - Get current user
- `Future<void> updateUser(User user)` - Update user info
- `Future<void> updateUserBalance(double emissions, double credits)` - Update totals

### 2. Transaction Service (`transaction_service.dart`)
- `Future<List<Transaction>> getAllTransactions()` - Get all transactions
- `Future<Transaction> getTransactionById(String id)` - Get single transaction
- `Future<void> addTransaction(Transaction transaction)` - Add new transaction
- `Future<List<Transaction>> getTransactionsByType(String type)` - Filter by type
- `Future<Map<String, double>> getStatistics()` - Get aggregated stats

### 3. Blockchain Service (`blockchain_service.dart`)
- `Future<String> submitToBlockchain(Transaction transaction)` - Submit to blockchain
- `Future<BlockchainRecord> getBlockchainRecord(String hash)` - Verify blockchain record
- `Future<bool> verifyTransaction(String hash)` - Verify transaction on blockchain
- `Future<String> generateWalletAddress()` - Generate new wallet
- `String getCurrentWalletAddress()` - Get current wallet
- Mock blockchain simulation for MVP (local storage + hash generation)

## Screen Structure (lib/screens)

### 1. Home Screen (`home_screen.dart`)
- Custom navigation structure (not Material Design)
- Tab-based or side navigation to access:
  - Dashboard
  - Record Emissions
  - Record Credits
  - Transactions

### 2. Dashboard Screen (`dashboard_screen.dart`)
- Cards showing:
  - Total Carbon Footprint
  - Total Carbon Credits
  - Net Balance (Credits - Emissions)
  - Recent Transactions (last 5)
- Visual charts/indicators
- Quick action buttons

### 3. Record Emission Screen (`record_emission_screen.dart`)
- Form to log emissions:
  - Category dropdown (Transportation, Energy, Industrial, etc.)
  - Amount input (in tons CO2)
  - Description/Notes
  - Date picker
- Submit to blockchain button
- Real-time validation

### 4. Record Credit Screen (`record_credit_screen.dart`)
- Form to log credits:
  - Category dropdown (Solar, Wind, Reforestation, etc.)
  - Amount input (in credits)
  - Description/Notes
  - Date picker
- Submit to blockchain button
- Real-time validation

### 5. Transactions Screen (`transactions_screen.dart`)
- List view of all transactions
- Filter by type (Emission/Credit)
- Sort by date
- Search functionality
- Each item shows:
  - Type icon and color
  - Amount
  - Category
  - Date
  - Blockchain status indicator
- Tap to view details

### 6. Transaction Detail Screen (`transaction_detail_screen.dart`)
- Full transaction information
- Blockchain verification details:
  - Transaction hash
  - Block number
  - Timestamp
  - Confirmations
- Copy hash button
- Status indicator
- Link to view on blockchain explorer (simulated)

## Widgets (lib/widgets)

### 1. Custom Navigation (`custom_navigation.dart`)
- Modern bottom navigation or side drawer
- Icon + label for each section
- Smooth transitions

### 2. Stat Card (`stat_card.dart`)
- Reusable card for displaying statistics
- Icon, label, value, trend indicator
- Custom styling with gradients

### 3. Transaction Card (`transaction_card.dart`)
- Reusable list item for transactions
- Type indicator, amount, category, date
- Blockchain status badge

### 4. Blockchain Badge (`blockchain_badge.dart`)
- Visual indicator of blockchain status
- Colors: pending (yellow), confirmed (green), failed (red)
- Animated when pending

### 5. Custom Button (`custom_button.dart`)
- Reusable button component
- Gradient backgrounds
- Ripple effects
- Loading states

### 6. Custom Input Field (`custom_input_field.dart`)
- Reusable form input
- Custom styling
- Validation indicators

## Blockchain Implementation Strategy

Since this is a frontend app, we'll implement a **simulated blockchain** with real blockchain characteristics:

1. **Hash Generation**: Use crypto package to generate SHA-256 hashes
2. **Block Simulation**: Create block structure with:
   - Previous hash
   - Current hash
   - Timestamp
   - Transaction data
   - Block number
3. **Local Storage**: Store blockchain data in shared_preferences
4. **Immutability**: Once recorded, transactions cannot be modified
5. **Verification**: Implement hash verification to ensure data integrity

## Implementation Steps

### Phase 1: Project Setup & Dependencies
1. Add required dependencies (web3dart, shared_preferences, http, crypto, intl, fl_chart)
2. Update theme.dart with custom color palette (eco-friendly greens, blues, gradients)
3. Configure permissions if needed

### Phase 2: Data Layer
4. Create all data models with toJson/fromJson/copyWith methods
5. Implement User Service with local storage
6. Implement Transaction Service with local storage
7. Implement Blockchain Service with hash generation and verification

### Phase 3: Reusable Widgets
8. Create custom navigation widget
9. Create stat card widget
10. Create transaction card widget
11. Create blockchain badge widget
12. Create custom button widget
13. Create custom input field widget

### Phase 4: Screen Implementation
14. Build Dashboard Screen with stats and recent transactions
15. Build Record Emission Screen with form
16. Build Record Credit Screen with form
17. Build Transactions Screen with list and filters
18. Build Transaction Detail Screen with blockchain info
19. Build Home Screen with navigation structure

### Phase 5: Integration & Testing
20. Connect all screens with navigation
21. Implement blockchain submission flow
22. Add sample data for testing
23. Test all user flows
24. Add loading states and error handling

### Phase 6: Polish
25. Add animations and transitions
26. Implement responsive design
27. Test on different screen sizes
28. Run dart analyze and fix errors

## Color Palette (Eco-Friendly Theme)
- **Primary**: Deep Forest Green (#0F4C3A)
- **Secondary**: Ocean Blue (#1E88E5)
- **Accent**: Bright Teal (#00BFA5)
- **Success**: Vibrant Green (#4CAF50)
- **Warning**: Amber (#FFA726)
- **Error**: Coral Red (#EF5350)
- **Background Light**: Off-White (#F8FAFB)
- **Background Dark**: Deep Navy (#0A1929)
- **Text Light**: Charcoal (#2C3E50)
- **Text Dark**: Light Gray (#E0E0E0)

## File Structure
```
lib/
├── main.dart
├── theme.dart
├── models/
│   ├── user_model.dart
│   ├── transaction_model.dart
│   └── blockchain_record_model.dart
├── services/
│   ├── user_service.dart
│   ├── transaction_service.dart
│   └── blockchain_service.dart
├── screens/
│   ├── home_screen.dart
│   ├── dashboard_screen.dart
│   ├── record_emission_screen.dart
│   ├── record_credit_screen.dart
│   ├── transactions_screen.dart
│   └── transaction_detail_screen.dart
└── widgets/
    ├── custom_navigation.dart
    ├── stat_card.dart
    ├── transaction_card.dart
    ├── blockchain_badge.dart
    ├── custom_button.dart
    └── custom_input_field.dart
```

## Notes
- The blockchain implementation is simulated but follows real blockchain principles
- All transactions are cryptographically hashed for integrity
- The system is designed to be extensible for real blockchain integration later
- Focus on beautiful, modern UI with generous spacing and smooth animations
