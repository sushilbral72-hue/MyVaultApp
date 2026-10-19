# Personal Vault (Android)

A minimal offline Android app scaffold for privately storing photos and documents.

## Features
- First-run PIN setup (4–12 digits), salted PBKDF2-HMAC-SHA256 PIN verification
- Files encrypted with AES-256-GCM; encryption key is generated and held by Android Keystore
- File picker uses Android's system document picker; no broad storage permission
- Encrypted files stored in app-private internal storage; offline operation; no network permission
- Open and delete stored files; lock button returns to PIN screen

## Build APK
1. Install Android Studio on a computer and ensure Android SDK Platform 35 is installed.
2. Open this folder in Android Studio and let Gradle sync.
3. Use **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
4. Debug APK is normally produced at `app/build/outputs/apk/debug/app-debug.apk`.

## Important security notes
- This is a starter project, not a professionally audited security product.
- PIN is stored as a salted PBKDF2 hash, not as plaintext. Encrypted files use a key in Android Keystore.
- Opening a file decrypts a temporary copy into the app cache and shares it with a compatible viewer. The viewer may copy or retain that decrypted copy; close/delete it in the viewer if sensitive.
- Uninstalling the app or clearing its data deletes the vault and its key. There is no recovery mechanism yet. Back up important originals separately.
- If you forget the PIN, there is no reset/recovery flow in this starter.
