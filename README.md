# EcoLedger - Carbon Credit Tracking System

https://7e44euqwtym0rp63q3u1.share.dreamflow.app/

A blockchain-based Carbon Credit Tracking System built with Flutter that records carbon emissions and credits with transparency and immutability.

## 🌟 Features

- **Blockchain Integration**: All transactions are recorded on a simulated blockchain with cryptographic hashing
- **Carbon Emission Tracking**: Log and monitor your carbon footprint
- **Carbon Credit Management**: Record carbon credits to offset emissions
- **Real-time Dashboard**: View your carbon balance and recent activities
- **Transaction History**: Browse all blockchain-verified transactions
- **Blockchain Verification**: Each transaction includes hash, block number, and verification details
- **Modern UI**: Beautiful, eco-friendly design with smooth animations

## 🛠️ Technology Stack

- **Framework**: Flutter 3.6+
- **State Management**: StatefulWidget (built-in)
- **Local Storage**: SharedPreferences
- **Blockchain Simulation**: SHA-256 cryptographic hashing with crypto package
- **Charts**: fl_chart for data visualization
- **Date Formatting**: intl package

## 📱 Screens

1. **Dashboard**: Overview of carbon emissions, credits, and net balance
2. **Transactions**: Complete list of all blockchain-recorded transactions
3. **Record Emission**: Form to log carbon emissions
4. **Record Credit**: Form to add carbon credits
5. **Transaction Details**: Detailed view with blockchain verification info

## 🔐 Blockchain Implementation

The app implements a simulated blockchain with real blockchain characteristics:

- **Hash Generation**: SHA-256 cryptographic hashing
- **Block Structure**: Sequential blocks with previous hash references
- **Immutability**: Once recorded, transactions cannot be modified
- **Verification**: Hash verification ensures data integrity
- **Wallet System**: Each user has a unique blockchain wallet address

## 🚀 Getting Started

### Prerequisites

- Flutter SDK 3.6 or higher
- Dart 3.6 or higher
- Android Studio / VS Code / Dreamflow

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/ecoledger.git
cd ecoledger
```

2. Install dependencies:
```bash
flutter pub get
```

3. Run the app:
```bash
flutter run
```

## 📦 Dependencies

```yaml
dependencies:
  flutter:
    sdk: flutter
  google_fonts: ^6.1.0
  shared_preferences: ^2.0.0
  crypto: ^3.0.0
  intl: 0.20.2
  fl_chart: 0.68.0
  uuid: ^4.0.0
```

## 📂 Project Structure

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

## 🎨 Design Philosophy

- **Non-Material Design**: Custom UI with modern aesthetics
- **Eco-Friendly Palette**: Deep forest greens, ocean blues, and bright teals
- **Generous Spacing**: Clean, uncluttered interface
- **Smooth Animations**: Interactive and engaging user experience
- **Accessibility**: High contrast and readable typography

## 🌍 Environmental Impact

EcoLedger helps organizations and individuals:
- Track their carbon footprint transparently
- Monitor carbon credit purchases and generation
- Maintain immutable environmental records
- Promote sustainability through blockchain accountability

## 🔮 Future Enhancements

- Real blockchain integration (Ethereum, Polygon, or custom chain)
- Multi-user support with authentication
- Data export and reporting features
- Integration with carbon credit marketplaces
- IoT device integration for automated emission tracking
- Carbon footprint predictions using ML

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/ecoledger/issues).

## 👨‍💻 Author

Built with 💚 for a sustainable future

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

**Note**: This app uses a simulated blockchain for demonstration purposes. For production use, integrate with a real blockchain network.
