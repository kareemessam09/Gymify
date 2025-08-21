# Gymify

Elevate your fitness journey with **Gymify** — a modern Android app that delivers personalized workout plans, intelligent exercise guidance, and seamless offline readiness. Built natively with Kotlin and architected for performance, scalability, and a delightful user experience.


## 📱 Screens
<table>
  <tr>
    <td><img src="https://raw.githubusercontent.com/kareemessam09/Gymify/master/gymify.png" alt="Gymify Home" width="200"></td>
    <td><img src="https://raw.githubusercontent.com/kareemessam09/Gymify/master/gymmmmm.png" alt="Gymify Exercises" width="200"></td>
    <td><img src="https://raw.githubusercontent.com/kareemessam09/Gymify/master/profile.png" alt="Profile" width="200"></td>
    <td><img src="https://raw.githubusercontent.com/kareemessam09/Gymify/master/chatt.png" alt="Chat Interface" width="200"></td>
    <td><img src="https://raw.githubusercontent.com/kareemessam09/Gymify/master/chatrespo.png" alt="Chat Response" width="200"></td>
  </tr>
  <tr>
    <td align="center">Gymify Home</td>
    <td align="center">Gymify Exercises</td>
    <td align="center">Profile</td>
    <td align="center">Chat Interface</td>
    <td align="center">Chat Response</td>
  </tr>
</table>

## 🚀 Feature Highlights
- Personalized onboarding (height, weight, BMI auto-computed via DataStore persistence)
- Dynamic workout plans (auto-generated or user-driven)
- Exercise catalog with detail screens (muscles, equipment, instructions)
- Plan progress tracking & session logging
- Offline access to cached exercises (Room fallback when network unavailable)
- Smart network handling (online fetch with graceful local fallback)
- Modern reactive UI (Jetpack Compose)
- Dark/Light theme readiness (Material Design System)
- Dependency injection via Hilt for clean modular construction
- Secure local preferences via Jetpack DataStore (replacing legacy SharedPreferences)
- Efficient pagination/lazy loading for large exercise sets
- Error & empty states with user-friendly messaging
- Extensible domain layers (repository pattern)
- Clean MVVM with unidirectional data flow (Flow/LiveData exposure)
- Kotlin Coroutines for structured concurrency
- Separation of concerns: API layer | local cache | domain mappers | presentation state
- Continuous improvement ready: analytics/notifications plug-in points

## 🧩 Architecture Overview
**Layered MVVM:**
- **UI Layer**: Composables/Activities observe immutable `StateFlow`/`LiveData`
- **ViewModels**: Orchestrate use cases, expose UI models, handle side effects
- **Repository Layer**: Mediates network (Retrofit) + local (Room) + DataStore
- **Data Layer**: DTOs, DAOs, API interfaces, mappers to domain models
- **Persistence**: Room for structured entities; DataStore for lightweight key/value profile metrics
- **DI Graph**: Hilt modules provide singletons (Retrofit, OkHttp, Room DB, Repos)

## 🛠 Tech Stack
- **Language**: Kotlin (Coroutines, Flow)
- **DI**: Hilt
- **Network**: Retrofit + OkHttp 
- **Persistence**: Room + DataStore Proto/Preferences
- **Concurrency**: Coroutines (viewModelScope)
- **UI**: Jetpack Compose 
- **Build**: Gradle


## 📂 Key Modules (Conceptual)
- `data/remote`: API services, DTOs
- `data/local`: Room entities, DAO, DataStoreManager
- `domain`: Models, mappers, repository abstractions
- `presentation`: ViewModels, UI state, composables/views
- `di`: Hilt modules for provisioning dependencies

## 🔐 Data & State
- Height/weight stored via DataStore (reactively streamed to ViewModels)
- Exercises cached locally for offline continuity
- Network errors surfaced through unified error channel and rendered gracefully

## 📡 Networking Strategy
- Attempt remote fetch (suspend Retrofit call)
- On failure or offline: fallback to Room cached entity set
- Minimal blocking; responses transformed to UI models before emission

## ⚙ Setup & Installation
1. Clone repo
2. Open in Android Studio (Arctic Fox+ / Narwhal recommended)
3. Create or verify `local.properties` (SDK paths)
4. Sync Gradle
5. Provide API base URL (if configurable) via `BuildConfig` or `Hilt` module
6. Run on device/emulator (API 24+ recommended)

