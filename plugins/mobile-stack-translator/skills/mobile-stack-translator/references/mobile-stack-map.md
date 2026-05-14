# Mobile Stack Map

Use this as a concise reference for explaining equivalents across Swift/iOS, Kotlin/Android, Flutter, and React Native. Prefer idiomatic target-stack concepts over literal syntax translation.

## UI Composition

| Concept | Swift/iOS | Kotlin/Android | Flutter | React Native |
| --- | --- | --- | --- | --- |
| Declarative UI unit | SwiftUI `View` | Compose `@Composable` | `Widget` | Function component |
| Imperative UI unit | `UIViewController`, `UIView` | `Activity`, `Fragment`, `View` | Usually avoided | Native module/view manager |
| Layout | SwiftUI layout modifiers, Auto Layout | Compose modifiers, XML/Views | Widget tree constraints | Flexbox styles |
| Styling | Modifiers, asset catalogs | Modifiers, resources, themes | `ThemeData`, widget params | `StyleSheet`, theme libraries |

## State And Rendering

| Concept | Swift/iOS | Kotlin/Android | Flutter | React Native |
| --- | --- | --- | --- | --- |
| Local view state | `@State` | `remember`, `mutableStateOf` | `State`, `setState` | `useState` |
| Parent-child binding | `@Binding` | state hoisting + callbacks | constructor value + callback | props + callback |
| Observable model | `@Observable`, `ObservableObject` | `ViewModel` with `StateFlow` | `ChangeNotifier`, Riverpod, Bloc | Context, Zustand, Redux, React Query |
| Side effects | `.task`, `.onAppear`, Combine | `LaunchedEffect`, lifecycle APIs | `initState`, effects in state tools | `useEffect` |

Explain who owns the state, what triggers re-rendering, and how long the state lives.

## Navigation

| Concept | Swift/iOS | Kotlin/Android | Flutter | React Native |
| --- | --- | --- | --- | --- |
| Stack navigation | `NavigationStack` | Navigation Compose / Fragment nav | `Navigator`, `go_router` | React Navigation stack |
| Route data | value routes, path params | route args, saved state handle | route objects, path params | params object |
| Deep links | Universal Links, URL handling | App Links, intents | Router integration | Linking + navigation config |

Call out whether navigation is state-driven, route-string-driven, or controller-driven in the specific code.

## Lifecycle

| Concept | Swift/iOS | Kotlin/Android | Flutter | React Native |
| --- | --- | --- | --- | --- |
| Screen appears | `.onAppear`, view controller callbacks | `onStart`, `onResume`, Compose effects | `initState`, route observers | focus events, `useEffect` |
| Screen disappears | `.onDisappear`, view controller callbacks | `onPause`, `onStop`, disposal effects | `dispose`, route observers | cleanup function, blur events |
| App lifecycle | `scenePhase`, app delegate | process/activity lifecycle | `WidgetsBindingObserver` | `AppState` |

Lifecycle names are not one-to-one. Explain the trigger and ownership rather than only matching method names.

## Async And Concurrency

| Concept | Swift/iOS | Kotlin/Android | Flutter | React Native |
| --- | --- | --- | --- | --- |
| One-shot async | `async`/`await`, `Task` | coroutines, `suspend` | `Future`, `async`/`await` | Promise, `async`/`await` |
| Streams | `AsyncSequence`, Combine | `Flow` | `Stream` | event emitter, Observable libraries |
| UI-thread updates | `MainActor` | Main dispatcher | main isolate | JS thread plus native bridge constraints |
| Cancellation | task cancellation | coroutine cancellation | subscription cancellation | effect cleanup, abort controllers |

Call out cancellation and thread/isolate/bridge boundaries. These are frequent sources of wrong translations.

## Persistence And Networking

| Concept | Swift/iOS | Kotlin/Android | Flutter | React Native |
| --- | --- | --- | --- | --- |
| HTTP | `URLSession` | Retrofit, Ktor, OkHttp | `http`, Dio | `fetch`, Axios, native modules |
| Key-value storage | `UserDefaults` | DataStore, SharedPreferences | shared_preferences | AsyncStorage or secure storage library |
| Database | SwiftData, Core Data, SQLite | Room, SQLite | Drift, Isar, sqflite | SQLite/WatermelonDB/Realm |
| Secure storage | Keychain | Keystore-backed storage | flutter_secure_storage | Keychain/Keystore wrappers |

Mention platform permissions, background behavior, serialization, and migration differences when relevant.

## Testing

| Concept | Swift/iOS | Kotlin/Android | Flutter | React Native |
| --- | --- | --- | --- | --- |
| Unit tests | XCTest, Swift Testing | JUnit, Kotlin test | `flutter test` | Jest |
| UI/component tests | XCUITest, ViewInspector | Espresso, Compose tests | widget tests | React Native Testing Library |
| End-to-end tests | XCUITest | Espresso, Maestro | integration_test, Patrol | Detox, Maestro |
| Async test concerns | expectations, clocks | coroutine dispatchers | fake async, pumps | fake timers, async utilities |

Translate testing strategy by behavior under test, not only by framework name.
