# Gymify

Elevate your fitness journey with **Gymify** — a modern Android app that delivers personalized workout plans, intelligent exercise guidance, and seamless offline readiness. Built natively with Kotlin and architected for performance, scalability, and a delightful user experience.

## ✨ Core Value Proposition
Gymify transforms raw fitness intent into structured, trackable progress. It blends smart data (BMI, goals, experience) with curated exercise libraries and adaptive plans, all wrapped in a clean, fast mobile experience.

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

## 📱 Screens (Planned/Existing)
- Onboarding/Metrics input
- Home Dashboard (BMI, today plan, quick actions)
- Exercise Library (filter, search, pagination)
- Exercise Detail (media, instructions)
- Plan Overview (cycle/week structure)
- Session Tracker (sets, reps, completion)
- Settings (theme, metrics update)

<table>
  <tr>
    <td><img src="docs/images/onboarding_metrics.png" alt="Onboarding/Metrics Input" width="200"></td>
    <td><img src="docs/images/home_dashboard.png" alt="Home Dashboard" width="200"></td>
    <td><img src="docs/images/exercise_library.png" alt="Exercise Library" width="200"></td>
    <td><img src="docs/images/exercise_detail.png" alt="Exercise Detail" width="200"></td>
    <td><img src="docs/images/plan_overview.png" alt="Plan Overview" width="200"></td>
    <td><img src="docs/images/session_tracker.png" alt="Session Tracker" width="200"></td>
    <td><img src="docs/images/settings.png" alt="Settings" width="200"></td>
  </tr>
  <tr>
    <td align="center">Onboarding/Metrics Input</td>
    <td align="center">Home Dashboard</td>
    <td align="center">Exercise Library</td>
    <td align="center">Exercise Detail</td>
    <td align="center">Plan Overview</td>
    <td align="center">Session Tracker</td>
    <td align="center">Settings</td>
  </tr>
</table>

## ⚙ Setup & Installation
1. Clone repo
2. Open in Android Studio (Arctic Fox+ / Narwhal recommended)
3. Create or verify `local.properties` (SDK paths)
4. Sync Gradle
5. Provide API base URL (if configurable) via `BuildConfig` or `Hilt` module
6. Run on device/emulator (API 24+ recommended)

