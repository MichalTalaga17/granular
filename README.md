# Granular – Inventory & Store Management App

[![Swift](https://img.shields.io/badge/Swift-5.9+-orange.svg)](https://swift.org)
[![Platform](https://img.shields.io/badge/Platform-iOS%20%7C%20iPadOS%20%7C%20macOS-blue.svg)](https://developer.apple.com)
[![Supabase](https://img.shields.io/badge/Backend-Supabase-green.svg)](https://supabase.com)

**Granular** is a modern inventory and order management application built for Apple platforms (iOS, iPadOS, macOS), using **Supabase** as the backend. It's designed for small and medium businesses like hardware stores and wholesalers to manage products, deliveries, stock movements, and customer orders — all in one intuitive system.

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Database Schema](#database-schema)
- [Usage](#usage)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)

## Features

- 🔐 User authentication with Supabase Auth
- 📦 Product and stock management with real-time updates
- 🚚 Delivery tracking and automatic stock adjustments
- 🧾 Order creation with VAT-calculated pricing
- 📁 File storage for invoices and delivery documents
- 📊 Dashboard with basic analytics and movement history
- 💻 Optimized for iPad and Mac with SwiftUI
- 🔄 Real-time synchronization across devices
- 🌐 Offline support with data sync

## Tech Stack

- **Frontend**: Swift + SwiftUI
- **Data Persistence**: SwiftData for local caching
- **Backend**: Supabase (PostgreSQL, Storage, Auth, RLS)
- **Architecture**: MVVM with async/await
- **Storage**: Supabase Storage for documents
- **Authentication**: Supabase email/password or magic link
- **Database**: PostgreSQL with Row Level Security (RLS)

## Prerequisites

Before you begin, ensure you have the following installed:

- **Xcode 15.0+** with iOS 17.0+ SDK
- **Swift 5.9+**
- **macOS Ventura 13.0+** (for development)
- **Supabase account** for backend services

### Supported Platforms

- iOS 17.0+
- iPadOS 17.0+
- macOS 14.0+

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/MichalTalaga17/granular.git
   cd granular
   ```

2. **Open in Xcode**
   ```bash
   open Granular.xcodeproj
   # or if using Swift Package Manager
   open Package.swift
   ```

3. **Configure Supabase** (see [Configuration](#configuration) section)

4. **Build and run**
   - Select your target device/simulator
   - Press `⌘+R` to build and run

## Getting Started

### Quick Start

1. **Set up Supabase project**
   - Create a new project at [supabase.com](https://supabase.com)
   - Note your project URL and anon key
   - Run the database schema (SQL files will be provided)

2. **Configure the app**
   - Add your Supabase credentials to the configuration
   - Build and run the project

3. **First launch**
   - Create an account or sign in
   - Start adding products and managing inventory

## Project Structure

```
Granular/
├── App/                    # App entry point and configuration
├── Features/               # Feature modules
│   ├── Authentication/     # Login, registration, user management
│   ├── Inventory/         # Product and stock management
│   ├── Orders/            # Order creation and management
│   ├── Deliveries/        # Delivery tracking
│   └── Dashboard/         # Analytics and overview
├── Shared/                # Shared components and utilities
│   ├── Models/            # Data models
│   ├── Services/          # API services and business logic
│   ├── Views/             # Reusable UI components
│   └── Utilities/         # Helper functions and extensions
├── Resources/             # Assets, localizations, etc.
└── Tests/                 # Unit and UI tests
```

*Note: Project structure will be updated as development progresses.*

## Configuration

### Supabase Setup

1. Create a `Config.swift` file in your project:
   ```swift
   enum Config {
       static let supabaseURL = "YOUR_SUPABASE_URL"
       static let supabaseAnonKey = "YOUR_SUPABASE_ANON_KEY"
   }
   ```

2. Add `Config.swift` to your `.gitignore` to keep credentials secure

3. Set up the database schema using the provided SQL migration files

### Environment Variables

For development, you can also use environment variables:
- `SUPABASE_URL`: Your Supabase project URL
- `SUPABASE_ANON_KEY`: Your Supabase anonymous key

## Database Schema

The application uses the following core tables in Supabase PostgreSQL:

### Core Tables

- **`users`**: User profiles and authentication data
- **`products`**: Product catalog with SKUs, descriptions, and pricing
- **`inventory`**: Current stock levels and locations
- **`orders`**: Customer orders with status tracking
- **`order_items`**: Individual items within orders
- **`deliveries`**: Delivery tracking and status updates
- **`stock_movements`**: Audit trail for all inventory changes
- **`categories`**: Product categorization system
- **`suppliers`**: Supplier information and contacts

### Key Relationships

- Products have many inventory records (for different locations)
- Orders contain multiple order items
- Deliveries are linked to orders and update inventory automatically
- Stock movements track all changes with timestamps and reasons

*Detailed SQL schema files will be provided in the `/database` directory as the project develops.*

## Usage

### Basic Operations

- **Adding Products**: Navigate to Inventory → Add Product
- **Managing Stock**: Use the stock management interface to track quantities
- **Creating Orders**: Go to Orders → New Order to create customer orders
- **Tracking Deliveries**: Monitor deliveries and automatically update stock levels
- **Analytics**: View business insights on the Dashboard

### Advanced Features

- **Bulk Operations**: Import/export product data
- **Reporting**: Generate custom reports for inventory and sales
- **Multi-user**: Collaborate with team members using role-based access

*Detailed usage documentation will be added as features are implemented.*

## Roadmap

### Phase 1: Foundation (Current)
- [x] Project setup and README documentation
- [ ] Xcode project structure and basic UI
- [ ] Supabase integration and authentication
- [ ] Core data models and database schema

### Phase 2: Core Features
- [ ] User authentication and registration
- [ ] Basic product management (CRUD operations)
- [ ] Inventory tracking and stock levels
- [ ] Simple order creation and management

### Phase 3: Advanced Features
- [ ] Delivery tracking with automatic stock updates
- [ ] File storage for invoices and documents
- [ ] Dashboard with analytics and reporting
- [ ] Multi-user support with role-based access

### Phase 4: Polish & Optimization
- [ ] Offline support with data synchronization
- [ ] Performance optimization
- [ ] Advanced reporting and exports
- [ ] App Store deployment

### Future Considerations
- [ ] Integration with external accounting systems
- [ ] Barcode scanning for product management
- [ ] Push notifications for low stock alerts
- [ ] API for third-party integrations

## Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Add tests for new functionality
5. Ensure all tests pass
6. Commit your changes (`git commit -m 'Add amazing feature'`)
7. Push to the branch (`git push origin feature/amazing-feature`)
8. Open a Pull Request

### Code Style

- Follow Swift API Design Guidelines
- Use SwiftLint for code formatting
- Write descriptive commit messages
- Add documentation for public APIs

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

### Getting Help

- 📖 [Documentation](https://github.com/MichalTalaga17/granular/wiki) (coming soon)
- 🐛 [Issue Tracker](https://github.com/MichalTalaga17/granular/issues)
- 💬 [Discussions](https://github.com/MichalTalaga17/granular/discussions)

### Contact

- **Email**: [michal.talaga@example.com](mailto:michal.talaga@example.com)
- **GitHub**: [@MichalTalaga17](https://github.com/MichalTalaga17)

---

**Made with ❤️ for small and medium businesses**