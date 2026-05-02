# Technology Stack

| Layer | Technology | Reason | Cost |
|-------|-----------|--------|------|
| **Mobile Framework** | React Native | Cross-platform development for iOS and Android from single codebase. Large community, excellent documentation, strong offline support with libraries like WatermelonDB. Junior-developer friendly with JavaScript/TypeScript. | Free |
| **UI Components** | React Native Paper | Material Design components optimized for mobile. Provides consistent, accessible UI elements out of the box. Supports theming for light/dark modes. | Free |
| **Local Database** | WatermelonDB | Built specifically for React Native with offline-first design. Lazy loading for performance with large datasets. Automatic sync capabilities. SQLite under the hood. | Open Source |
| **State Management** | Zustand | Lightweight, simple state management without boilerplate. Easy to learn for junior developers. Perfect for small to medium apps. | Open Source |
| **Navigation** | React Navigation | Standard navigation library for React Native. Supports stack, tab, and drawer navigation patterns. Well-documented and maintained. | Free |
| **Charts/Visualization** | Victory Native | Declarative charting library for React Native. Supports pie, line, and bar charts. Customizable and performant. | Open Source |
| **Authentication** | Supabase Auth | Free tier includes 50,000 monthly active users. Built-in email/password auth. Open source alternative to Firebase. | Free |
| **Cloud Database** | Supabase PostgreSQL | Free tier includes 500MB database, more than sufficient for single-user transaction data. Automatic backups. Real-time capabilities if needed later. | Free |
| **Cloud Sync Backend** | Supabase Realtime | Built into Supabase, provides real-time sync capabilities. Can implement custom sync logic using Supabase client libraries. | Free |
| **Encryption (Local)** | react-native-encrypted-storage | Secure key-value storage using device keychain/keystore. Encrypts data at rest automatically. | Open Source |
| **Encryption (Transit)** | HTTPS/TLS | Built into Supabase and standard HTTP clients. Encrypts all data in transit. | Free |
| **Data Export/Import** | react-native-fs + papaparse | File system access for reading/writing CSV/JSON files. Papaparse for CSV parsing. Both well-maintained libraries. | Open Source |
| **Offline Detection** | @react-native-community/netinfo | Reliable network state detection. Integrates easily with sync logic. | Open Source |
| **Development Tools** | Expo (optional) | Simplifies React Native development with managed workflow. Provides easy testing on physical devices. Can eject if native modules needed. | Free |
| **Version Control** | Git + GitHub | Industry standard for source control. Free hosting for open source projects. | Free |
| **CI/CD** | GitHub Actions | Free tier includes 2,000 minutes/month. Automate testing and builds. | Free |
| **Hosting (Web Admin)** | Vercel or Netlify | If web dashboard needed later. Both offer generous free tiers. Not required for MVP. | Free |

## Stack Justification

### Mobile Framework Choice
React Native selected over Flutter or native development because:
- JavaScript/TypeScript is more accessible to junior developers than Dart or Swift/Kotlin
- Massive ecosystem of libraries and solutions for common problems
- Excellent offline-first libraries (WatermelonDB) built specifically for this use case
- Can share code with web version if needed later
- Strong community support in East Africa

### Database Choice
WatermelonDB over raw SQLite or Realm because:
- Built specifically for React Native offline-first apps
- Handles sync complexity out of the box
- Lazy loading prevents performance issues with large datasets
- Active development and good documentation
- Integrates seamlessly with Supabase for cloud sync

### Backend Choice
Supabase over Firebase or custom backend because:
- Completely open source (can self-host if needed)
- More generous free tier than Firebase
- PostgreSQL is more powerful and familiar than Firestore
- Built-in authentication and real-time capabilities
- Row-level security for data protection
- No vendor lock-in

### Chart Library Choice
Victory Native over react-native-chart-kit because:
- More actively maintained
- Better TypeScript support
- More customization options
- Declarative API matches React patterns
- Good performance with reasonable dataset sizes

## Development Environment Requirements

- Node.js 18+ (LTS)
- npm or yarn
- React Native CLI or Expo CLI
- Android Studio (for Android development)
- Xcode (for iOS development, macOS only)
- Git
- Code editor (VS Code recommended)

## Estimated Monthly Costs

| Service | Free Tier Limit | Expected Usage | Cost |
|---------|----------------|----------------|------|
| Supabase Database | 500MB | <10MB (single user) | $0 |
| Supabase Auth | 50,000 MAU | 1 user | $0 |
| Supabase Bandwidth | 2GB | <100MB/month | $0 |
| GitHub Actions | 2,000 minutes | <500 minutes | $0 |
| **Total** | | | **$0/month** |

All services remain free indefinitely for single-user usage. Costs only apply if scaling to multiple users or exceeding free tier limits.