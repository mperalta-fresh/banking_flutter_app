# banking_flutter_app

A new Flutter project.

# Architecture

Based on the *Separation of Concerns (SoC)* design principle—which promotes dividing a program into distinct sections by encapsulating information within components that expose well-defined interfaces—this project uses the MVVM architecture pattern, following recommendations from the [Flutter architecture](https://docs.flutter.dev/app-architecture/guide) documentation.

This projetc is split into two broad layers, the UI layer and the Data layer.

### UI layer
  Responsable of interactions with the user. 

  * **Views**: composition of widgets that shouldn't contain bussiness logic. Pass events in response to user interactions
  * **View models**: contains the logic that converts app data into UI state.

### Data layer
  * **Repositories**: responsible for polling data from services, and transforming that raw data into domain models.
  * **Services**: wrap API endpoints and expose asynchronous response objects.

![Architecture diagram](/assets/architecture_app.png)

The following is how the code is organized combining organization by *feature* and by *type*, Data layer aren't tied to a single feature, while UI layer are.

```

lib
├─┬─ presentation
│ ├─┬─ core
│ │ ├─┬─ shared_widgets
│ │ │ └─── <widget_name>.dart
│ │ └─┬─ themes
│ │   └─── <app_theme>.dart
│ └─┬─ <FEATURE NAME>
├───├─── screens
│   ├─┬─ view_model
│   │ └─── <view_model class>.dart
│   └─┬─ widgets
│     ├── <feature name>_screen.dart
│     └── <other widgets>
├─┬─ domain
│ └─┬─ models
│   └─── <model name>.dart
├─┬─ data
│ ├─┬─ repositories
│ │ └─── <repository class>.dart
│ ├─┬─ services
│ │ └─── <service class>.dart
│ └─┬─ model
│   └─── <api model class>.dart
├─── config
├─── utils
├─── routing
└─── main.dart

// The test folder contains unit and widget tests
test
├─── data
├─── domain
├─── ui
└─── utils

```