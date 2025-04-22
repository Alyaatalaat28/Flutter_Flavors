# Flutter Flavors Starter Kit

A production-ready implementation of Flutter flavors for managing multiple environments (dev, staging, prod) with complete Android and iOS setup.

## 📖 Learn More
For a complete guide to Flutter flavors, check out my in-depth article:  
[**Mastering Flutter Flavors: A Comprehensive Guide**](https://medium.com/@alyaatalaat205/understanding-flavors-in-flutter-a-step-by-step-guide-153b96e506af)


## 🚀 Key Features
- Pre-configured flavor system for Android & iOS
- Environment-specific app naming and configurations
- Sample entry points for each flavor
- CI/CD ready structure
- Easy customization for your projects

## ⚙️ Android Configuration
Pre-configured in `android/app/build.gradle`:

```gradle
flavorDimensions "environment"
productFlavors {
    dev {
        dimension "environment"
        applicationIdSuffix ".dev"
        resValue "string", "app_name", "MyApp Dev"
    }
    staging {
        dimension "environment"
        applicationIdSuffix ".staging"
        resValue "string", "app_name", "MyApp Staging"
    }
    prod {
        dimension "environment"
        resValue "string", "app_name", "MyApp"
    }
}
```

![flavors-android-icons](https://github.com/user-attachments/assets/36788e52-4582-4021-9132-399b9eafbf0f)


##  iOS Configuration
1. Open `ios/Runner.xcworkspace` in Xcode
2. Create schemes for each flavor (Dev, Staging, Prod)
3. Configure unique bundle identifiers per scheme

   <img width="972" alt="flavors-ios-schemes" src="https://github.com/user-attachments/assets/9237bd0c-92a6-4a8d-8970-7771a9f51361" />
   <img width="974" alt="flavors-ios-scheme-configurations" src="https://github.com/user-attachments/assets/d4ed190d-d945-4e54-bbf1-ea28f25b4d97" />
   
   ![flavors-ios-icons](https://github.com/user-attachments/assets/40b9cf04-fb24-426f-9771-c8fa22e8de38)



## 🏃 Running the App

### Android Commands
```bash
# Dev environment
flutter run --flavor dev -t lib/main_dev.dart

# Production environment
flutter run --flavor prod -t lib/main_prod.dart
```

### iOS Commands
```bash
# Dev environment
flutter run --flavor dev -t lib/main_dev.dart --scheme Dev

# Production environment
flutter run --flavor prod -t lib/main_prod.dart --scheme Prod
```

## 🛠 Building for Release

### Android
```bash
# Development APK
flutter build apk --flavor dev -t lib/main_dev.dart

# Production App Bundle
flutter build appbundle --flavor prod -t lib/main_prod.dart
```

### iOS
```bash
# Development build
flutter build ios --flavor dev -t lib/main_dev.dart --scheme Dev

# Production archive
flutter build ipa --flavor prod -t lib/main_prod.dart --scheme Prod
```

## 📁 Project Structure
```
lib/
├── main.dart          # Common app logic
├── main_dev.dart      # Dev environment entry
├── main_staging.dart  # Staging environment entry
├── main_prod.dart     # Production environment entry
└── config/
    ├── development.dart       # Dev configurations
    ├── staging.dart   # Staging configurations
    └── production.dart      # Production configurations
```

## 🛠 Troubleshooting

**Flavor not recognized?**  
- Verify flavors in both `build.gradle` and Xcode schemes
- Ensure correct flavor names in commands

**App name not changing?**  
Confirm `AndroidManifest.xml` uses:
```xml
<application android:label="@string/app_name">
```

## 📚 Additional Resources
- [Flutter Official Flavors Documentation](https://docs.flutter.dev/deployment/flavors)
- [Android Build Variants](https://developer.android.com/studio/build/build-variants)
