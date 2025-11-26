# SOAPCompteApp (Kotlin Android)

A complete Android application for managing bank accounts via SOAP protocol.

## Project Structure

```
SOAPCompteApp/
├── app/
│   ├── src/main/
│   │   ├── java/ma/projet/soapclient/
│   │   │   ├── MainActivity.kt          # Main entry point
│   │   │   ├── beans/
│   │   │   │   └── Compte.kt            # Data models
│   │   │   ├── ws/
│   │   │   │   └── Service.kt           # SOAP service calls
│   │   │   └── adapter/
│   │   │       └── CompteAdapter.kt     # RecyclerView adapter
│   │   └── res/
│   │       ├── layout/
│   │       │   ├── activity_main.xml    # Main screen layout
│   │       │   ├── item.xml             # List item layout
│   │       │   └── popup.xml            # Add account dialog
│   │       └── values/
│   │           ├── colors.xml           # Color definitions
│   │           └── styles.xml           # Theme styles
│   └── build.gradle                     # Module dependencies
├── build.gradle                         # Root build config
├── settings.gradle                      # Gradle settings
└── README.md                            # This file
```

## Setup Instructions

### 1. Create a new Android Studio project (if starting fresh)
- **Name:** SOAPCompteApp
- **Package name:** ma.projet.soapclient
- **Language:** Kotlin
- **Minimum SDK:** API 21 (Android 5.0)

### 2. Copy the provided files
- Copy all source files from `app/src/main/java/` to your project's `app/src/main/java/`
- Copy all layout files from `app/src/main/res/layout/` to your project's `app/src/main/res/layout/`
- Copy resource files (`colors.xml`, `styles.xml`) to `app/src/main/res/values/`

### 3. Update Gradle files
Replace or merge the contents of:
- `app/build.gradle` – includes Material Components, ksoap2, and Coroutines dependencies
- `build.gradle` (root) – plugin configurations
- `settings.gradle` – module settings

### 4. Sync Gradle
- Click **"Sync Now"** when prompted in Android Studio
- Wait for the dependency download to complete

### 5. Update SOAP endpoint (if needed)
In `app/src/main/java/ma/projet/soapclient/ws/Service.kt`, adjust:
```kotlin
private val URL = "http://10.0.2.2:8082/services/ws"
```

> **Note:** `10.0.2.2` is the emulator's way of accessing the host machine's localhost.
> If using a physical device, replace with your server's actual IP address.

### 6. Build & Run
- Connect an emulator or Android device
- Click **Run** in Android Studio
- The app will load the list of accounts from the SOAP service

## Features

✅ **List Accounts** – Fetch and display bank accounts from SOAP service  
✅ **Add Account** – Create new account with balance and type (COURANT/EPARGNE)  
✅ **Delete Account** – Remove account with confirmation dialog  
✅ **Responsive UI** – Material Design components with RecyclerView optimization  
✅ **Network Operations** – Coroutine-based async SOAP calls  

## Technology Stack

- **Language:** Kotlin
- **UI Framework:** Android Material Components
- **Web Service:** ksoap2-android (SOAP client)
- **Async:** Kotlin Coroutines
- **Layout:** ConstraintLayout + RecyclerView

## Important Notes

- Ensure your SOAP server is running before launching the app
- Network calls run on background thread (`Dispatchers.IO`)
- UI updates occur on main thread (`Dispatchers.Main`)
- Error handling via Toast notifications

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **Gradle sync fails** | Check internet connection; verify SDK installation |
| **SOAP connection error** | Verify server URL and ensure server is running |
| **No accounts displayed** | Check server response format matches expected SOAP structure |
| **Emulator cannot reach server** | Ensure you're using `10.0.2.2` for emulator or actual IP for device |
