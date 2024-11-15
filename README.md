# README.google_play_store
# To upload you flutter app on the google play console:-
1. You need to make changes in the project to make a release build
   In android/app/build.gradle file add this code :-
   ''' signingConfigs {
        release {
            keyAlias = keystoreProperties['keyAlias']
            keyPassword = keystoreProperties['keyPassword']
            storeFile = keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
            storePassword = keystoreProperties['storePassword']
        }
    }
    buildTypes {
        release {
            // signingConfig = signingConfigs.debug
            //for release use this code...
            signingConfig = signingConfigs.release
            minifyEnabled true // Enable ProGuard for release build
            shrinkResources true // Reduce resource size
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }'''

  This will make the app run in release mode.

2. Now create a .aab bundle file to release on google play store
   ''' flutter build appbundle --release '''

3. Then login to the google play store and create a new app

   (0) Go to the Google Play Console and select All Apps > Create App.
   (0) Enter the App Name, Default Language, and App or Game. Choose Free or Paid based on your app.
   (0) Accept the Developer Program Policies and click Create App.

4. Set Up Your App’s Store Listing:-
   
    -->Go to the App Content section, fill in necessary details such as Privacy Policy, Content Rating, and Target Audience.
    Store Listing:
    -->Provide a short and full description of your app.
    -->Add graphics such as app icons, screenshots, and a feature graphic.
    -->Categorization: Choose the appropriate category and tags for your app.

5. Upload the Android App Bundle (AAB):--
   
    -->Go to Release > Production > Releases.
    -->Click Create New Release.
    -->In the App Bundles and APKs section, click Upload and select the app-release.aab file generated earlier.
    -->Google Play Console will validate the uploaded file. If there are any errors, address them before proceeding.

   Then after send the app for review.(take 3-7 days usually):-
