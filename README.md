# Rento Finals

Rento Finals is a mobile car rental app built with Expo Router and Firebase. It provides onboarding, authentication, browsing/searching cars, booking flow with add-ons, and simulated payments (Credit Card, PayPal, GCash). It also includes user profiles, favorites, notifications, and an admin dashboard.

![Rento app preview](assets/rento.png)

## Features
- **Onboarding & Auth**: Welcome carousel, register, login, OTP flow.
- **Car Discovery**: Browse featured cars, search with brand filters, view car details and reviews.
- **Bookings**: Create bookings with duration, pickup location, add-ons, and taxes.
- **Payments**: Simulated payment flows (Credit Card, PayPal, GCash) that update booking status.
- **Favorites**: Like/unlike cars and view saved items.
- **Profile**: Manage personal info, payment methods, driver’s license, history, and settings.
- **Admin**: Manage cars, view bookings, users, and reports.

## Tech Stack
- **Expo** + **React Native** + **Expo Router**
- **Firebase** (Auth + Firestore)
- **TypeScript**
- UI libraries: **@expo/vector-icons**, **react-native-chart-kit**, **react-native-maps**, **react-native-reanimated**

## App Routes (high level)
- `/` – Welcome carousel
- `/login`, `/register`, `/otp`
- `/(tabs)` – Home, Search, Bookings, Profile
- `/car-details/[id]` – Car details & reviews
- `/checkout` – Booking + add-ons + payment selection
- `/credit-card`, `/paypal`, `/gcash` – Payment flows
- `/likedcars`, `/notifications`, `/developers`, `/admin`
- `/profile/*` – Personal info, license, payment, history, settings, support

## Project Structure
```
app/                 # Expo Router screens
  (tabs)/            # Bottom tabs: Home, Search, Bookings, Profile
  car-details/       # Dynamic car details route
  profile/           # Profile sub-routes
components/          # UI components
config/              # Firebase config
data/                # Static car data
hooks/               # App hooks (auth, bookings, cars, notifications)
types/               # TypeScript types
utils/               # Shared helpers/constants
assets/              # Images and branding
```

## Firebase Data Model (current usage)
- **users**: profile data, role flags
- **cars**: admin-managed inventory
- **bookings**: booking records with payment metadata
- **reviews**: car reviews
- **likedCars**: user favorites

Collections are accessed in the app screens and hooks. See firebase setup in config/firebase.ts.

## Setup
1. Install dependencies:
	- `npm install`
2. Update Firebase configuration in `config/firebase.ts` with your own project keys.
3. Start the app:
	- `npm run start`

### Run Targets
- Android: `npm run android`
- iOS: `npm run ios`
- Web: `npm run web`

## Scripts
- `start` – start Expo
- `android` – start and open Android emulator
- `ios` – start and open iOS simulator
- `web` – start web build
- `test` – run Jest

## Notes
- Admin access is protected by a simple password prompt in the login screen (default: `ADMIN123`).
- Payment screens are mock flows that write payment metadata to Firestore.
- Some content uses demo data (cars list, notifications).

## License
MIT
