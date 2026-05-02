# System Components

| Component | Responsibility | Connects To | Supports (FR-IDs) |
|-----------|---------------|------------|-------------------|
| **Mobile UI Layer** | Provides touch-optimized interface for transaction entry, budget management, and report viewing. Handles user input validation and visual feedback. | Local Data Manager, Chart Renderer | FR-001 to FR-008, FR-014 to FR-018, FR-025 |
| **Local Data Manager** | Manages all CRUD operations on local SQLite database. Primary data store for offline-first operation. Handles data persistence and retrieval. | Mobile UI Layer, Sync Engine, Local Database | FR-001 to FR-008, FR-009 to FR-013, FR-014 to FR-018, FR-026, FR-027 |
| **Local Database (SQLite)** | Stores all user data locally on device including transactions, categories, budgets. Encrypted at rest for security. | Local Data Manager | FR-001 to FR-034 |
| **Sync Engine** | Manages background synchronization between local database and cloud storage. Handles conflict resolution using last-write-wins strategy. Monitors connectivity and triggers sync. | Local Data Manager, Cloud Sync Service, Connectivity Monitor | FR-028, FR-029, FR-030 |
| **Connectivity Monitor** | Detects network availability and notifies Sync Engine when connection is restored. Provides sync status to UI. | Sync Engine, Mobile UI Layer | FR-030 |
| **Cloud Sync Service** | Backend service that receives and stores user data in cloud database. Handles authentication and data encryption in transit. | Sync Engine, Cloud Database | FR-028, FR-029, FR-030 |
| **Cloud Database** | Cloud-hosted database storing backup copy of user data. Enables data recovery and multi-device access. | Cloud Sync Service | FR-028, FR-029 |
| **Authentication Service** | Manages user registration, login, and session management. Provides secure access to cloud sync. | Mobile UI Layer, Cloud Sync Service | Security NFR |
| **Category Manager** | Handles category CRUD operations, provides predefined categories, manages custom categories. | Local Data Manager, Mobile UI Layer | FR-009 to FR-013 |
| **Budget Calculator** | Calculates spending against budget limits, generates warnings and alerts. Computes category and overall budget status. | Local Data Manager, Mobile UI Layer | FR-014 to FR-018 |
| **Report Generator** | Aggregates transaction data for specified time periods. Calculates totals, balances, and category breakdowns. | Local Data Manager, Chart Renderer | FR-019 to FR-025 |
| **Chart Renderer** | Generates visual charts (pie, line, bar) from report data. Provides interactive data visualization. | Report Generator, Mobile UI Layer | FR-022, FR-023 |
| **Data Export/Import Handler** | Converts data between internal format and CSV/JSON. Validates imported data format. | Local Data Manager, Mobile UI Layer | FR-031 to FR-034 |
| **Encryption Module** | Encrypts local database and data in transit. Handles key management for device storage. | Local Database, Sync Engine | Security NFR |