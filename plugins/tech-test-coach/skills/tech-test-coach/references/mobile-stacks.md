# Mobile Stack Coaching

Use this reference when a tech test is a mobile app. Keep the core coaching loop the same, but adapt hypotheses, verification, and hints to the stack.

## Shared Mobile Questions

Start with:

- What is the user-visible symptom: crash, wrong screen, stale data, bad layout, slow interaction, failed test, or broken navigation?
- Is the failure in UI state, data fetching, persistence, threading, lifecycle, dependency injection, navigation, or build configuration?
- What is the smallest reproduction: unit test, component/widget preview, simulator/emulator action, or one screen path?
- Are there platform constraints: no external libraries, protected files, minimum OS/API level, offline behavior, accessibility, or hidden tests?

## iOS / Swift / SwiftUI

Signals:

- `.xcodeproj`, `.xcworkspace`, `Package.swift`, `*.swift`, XCTest files

Coach around:

- SwiftUI ownership: `@State`, `@Binding`, `@StateObject`, `@ObservedObject`, `@EnvironmentObject`
- view identity and `ForEach` IDs
- navigation state and sheet presentation
- retain cycles in closures, Combine subscriptions, timers, delegates, and tasks
- main actor updates after async work
- XCTest expectations, async tests, and timing-based concurrency tests

Good hint prompts:

- "Which object owns this observable state for the lifetime of the screen?"
- "Does this async result return to the main actor before touching UI state?"
- "Would SwiftUI recreate this object during a body recomputation?"

## Android / Kotlin / Jetpack Compose

Signals:

- `build.gradle`, `settings.gradle`, `AndroidManifest.xml`, `*.kt`, `src/test`, `src/androidTest`

Coach around:

- Compose state: `remember`, `rememberSaveable`, `StateFlow`, `LiveData`, immutable UI state
- ViewModel lifecycle and coroutine scopes
- dispatcher choice: Main, IO, Default, test dispatchers
- recomposition and unstable parameters
- navigation back stack and saved state
- unit tests with coroutines, fake repositories, and virtual time

Good hint prompts:

- "Which scope owns this coroutine, and should it survive the screen leaving composition?"
- "Is this value remembered, derived, or recreated on every recomposition?"
- "What dispatcher does the test control, and what work escapes it?"

## Flutter / Dart

Signals:

- `pubspec.yaml`, `lib/`, `test/`, `*.dart`, `android/`, `ios/`

Coach around:

- widget state lifecycle: `initState`, `didUpdateWidget`, `dispose`, `setState`
- `FutureBuilder`/`StreamBuilder` repeated work and snapshot states
- provider/bloc/notifier ownership when present
- async gaps, mounted checks, and cancellation
- layout constraints: unbounded height, overflow, intrinsic sizing
- widget tests with `pump`, `pumpAndSettle`, fake async, and finders

Good hint prompts:

- "What creates this Future, and how often is the widget rebuilt?"
- "Could this callback fire after the widget is disposed?"
- "Which parent is providing the missing layout constraint?"

## React Native / TypeScript

Signals:

- `package.json`, `metro.config.*`, `android/`, `ios/`, `*.tsx`, Jest tests

Coach around:

- component state, props, memoization, and stale closures
- `useEffect` dependencies and cleanup
- navigation params and screen focus effects
- bridge/native module boundaries
- list identity and `keyExtractor`
- async storage/network mocks and Jest fake timers
- platform-specific files like `.ios.tsx` and `.android.tsx`

Good hint prompts:

- "Which render created this closure, and what values did it capture?"
- "Should this effect run on mount, on focus, or whenever this dependency changes?"
- "Does this list item have stable identity across updates?"

## When To Split This File

Keep this file as one reference until a stack needs detailed procedures, commands, or repeated patterns over roughly 150 lines. Then split into focused references such as:

- `references/ios-swift.md`
- `references/android-kotlin.md`
- `references/flutter-dart.md`
- `references/react-native.md`

Do not create empty or speculative stack files.
