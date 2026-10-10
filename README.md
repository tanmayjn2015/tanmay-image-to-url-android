# Tanmay Image to URL — Android wrapper

This is an Android Studio project for your hosted Flask web app:

**https://tanmay-image-to-url.wispbyte.app/**

It keeps image storage and URL generation on your existing server. The Android app is a native WebView shell with a branded launcher icon/splash screen, a loading bar, back navigation, and Android document-picker support for `<input type="file">` image uploads.

## Build on Android Studio

1. Install the current stable Android Studio and JDK 17.
2. Extract this ZIP.
3. In Android Studio choose **Open**, then select the extracted `image_to_url_android` folder.
4. Allow Gradle sync. Install Android SDK Platform 36 if prompted.
5. For a test APK choose **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. The debug APK is normally at `app/build/outputs/apk/debug/app-debug.apk`. Install it on your phone and test sign-in, selecting an image, uploading, copying the returned URL, sharing, and Android Back.

## Create a Play Store release

1. In Android Studio choose **Build → Generate Signed Bundle / APK**.
2. Choose **Android App Bundle** for Play Store, create and securely back up a signing key, then generate a release bundle.
3. The output is normally under `app/release/` or `app/build/outputs/bundle/release/` depending on Android Studio version.
4. In [Google Play Console](https://play.google.com/console/) create the app, complete the store listing and App content declarations, upload the signed `.aab`, and follow the testing/review steps shown in your account.

## Before publishing

- Test on several Android screen sizes and with slow/offline connections.
- Confirm the website works correctly in Android WebView, including login, upload, direct-link display, copy, and share.
- Publish a real privacy policy URL and complete Data safety, content rating, target audience, ads, and app-access declarations truthfully.
- Make sure you own or have permission to distribute the website, images, logo, and all content.
- Google Play can reject apps that offer little beyond a website wrapper or have broken/incomplete functionality. Consider adding Android-specific value and review the current Play policies before submission.
- This project uses `applicationId` `app.tanmay.imagetourl`. If you have already published an app under another package ID, use that existing ID instead; package IDs cannot be changed for updates.
- The server must remain online for the app to work. This wrapper does not host images itself and does not change your Flask backend.

## Important implementation notes

- HTTPS-only network policy; cleartext HTTP is disabled.
- JavaScript and DOM storage are enabled because typical Flask web interfaces need them.
- Android's system document picker is used for image selection. The app does not request broad storage permission.
- Site links stay inside the WebView; non-web URI schemes are passed to another app when available.
- The website's upload size/type restrictions and privacy/security remain enforced by your server. Check your Flask upload validation, authentication, retention, and public-link access rules before release.

## Project settings

- App name: Image to URL
- Version: 1.0.0 (versionCode 1)
- Minimum Android: Android 6.0 (API 23)
- Compile/target SDK: API 36
- Java: 17
