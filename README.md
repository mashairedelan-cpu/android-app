# Dmashy Gases Offline Android App

Native Android Java project for an offline-first gas-sales and wage-management app.

## What is included
- Offline SQLite database (`dmashy_gases.db`)
- User PIN default: `1234`
- Admin PIN default: `0000`
- Locked opening and closing records
- Admin-only locked-record edit with reason and audit trail
- Daily kg sold / expected money / actual money / shortage / surplus calculations
- Daily and weekly shortage warnings
- Weekly wage estimator and admin wage recording
- Wage received confirmation screen that blocks user workflow until confirmed
- Admin dashboard, daily history, audit trail, wage payment history
- Admin-only profit calculator with rent, transport, buying cost, wages and expenses
- SQLite backup to the app external files backup folder
- Protected XLSX export for latest locked report

## Logo note
No image file was present in the upload folder when this package was created, so the project contains a colored vector logo placeholder in `app/src/main/res/drawable/dmashy_logo.xml`. Replace that file with the provided Dmashy Gas & Equipment logo asset to use the official logo. The header uses only the logo plus section title and does not add extra black text under it.

## Build APK
Open the folder in Android Studio and choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

Or run from a machine with Android SDK + Gradle available:

```bash
gradle assembleDebug
```

The APK will be produced at:

```text
app/build/outputs/apk/debug/app-debug.apk
```

This app uses no internet permission and stores all records locally.

## Test data expected result
Opening: PROF, price 1.75, Tank 1 85, Tank 2 92, Tank 3 76.
Closing: Tank 1 60, Tank 2 80, Tank 3 70, cash 75.25, mobile 0, expenses 0.

Expected result:
- Tank 1 sold = 25kg
- Tank 2 sold = 12kg
- Tank 3 sold = 6kg
- Total kg sold = 43kg
- Expected money = $75.25
- Actual money = $75.25
- Shortage = $0.00
- Surplus = $0.00

Profit test defaults:
- Tank kg = 55
- Buying price per kg = 1.40
- Transport per refill = 4
- Monthly rent = 25
- Cost per kg = 1.40 + 4/55 = about 1.47
- Gas cost for 43kg = about $63.21
- Gross profit = about $12.04

## Build online with GitHub Actions, without Android Studio
This project includes `.github/workflows/build-apk.yml`.

Steps:
1. Create a new GitHub repository.
2. Upload all files from this project folder to the repository.
3. Open the repository on GitHub.
4. Go to **Actions**.
5. Click **Build Dmashy Gases APK**.
6. Click **Run workflow**.
7. Wait for the build to finish.
8. Open the completed workflow run.
9. Under **Artifacts**, download **Dmashy-Gases-debug-apk**.
10. Unzip it to get the APK file.
11. Copy the APK to your Android phone and install it.

If the phone blocks installation, enable **Install unknown apps** for the file manager/browser you are using, then install again.
