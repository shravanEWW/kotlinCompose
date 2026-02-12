# Senior Android Developer Interview README (Kotlin + Jetpack Compose)

This README contains **common interview topics with clear answers** for
Senior Android Developer roles.

------------------------------------------------------------------------

## 1. Kotlin Basics

### Q: What is a data class?

A: A data class is used to hold data. Kotlin automatically generates
`equals()`, `hashCode()`, `toString()`, and `copy()` functions.

### Q: What is a sealed class and where do you use it?

A: A sealed class is used to represent restricted class hierarchies. In
Android, it is commonly used for UI states like `Loading`, `Success`,
and `Error`.

### Q: Difference between `object`, `class`, and `companion object`?

A: - `class`: Normal class, multiple instances allowed. - `object`:
Singleton, only one instance. - `companion object`: Static-like object
inside a class.

### Q: Difference between `lateinit` and `lazy`?

A: - `lateinit`: Used with var, initialized later, non-null. - `lazy`:
Used with val, initialized only when first used.

------------------------------------------------------------------------

## 2. Coroutines

### Q: What is a suspend function?

A: A suspend function is a function that can be paused and resumed
without blocking the thread.

### Q: Difference between `launch` and `async`?

A: - `launch`: Fire-and-forget, does not return result. - `async`:
Returns a result using `await()`.

### Q: What is `viewModelScope`?

A: It is a CoroutineScope tied to ViewModel lifecycle. Coroutines are
cancelled when ViewModel is cleared.

### Q: What is Flow?

A: Flow is a cold asynchronous data stream that can emit multiple values
over time.

### Q: Difference between StateFlow and SharedFlow?

A: - StateFlow: Holds and emits the latest state. - SharedFlow: Used for
events like navigation or toasts.

------------------------------------------------------------------------

## 3. Jetpack Compose

### Q: What is a Composable?

A: A Composable is a function annotated with `@Composable` used to
describe UI.

### Q: What is recomposition?

A: Recomposition is when Compose re-executes composable functions to
update UI when state changes.

### Q: What is state hoisting?

A: Moving state to a parent composable and passing it down with events
to make composables reusable and testable.

### Q: Difference between `remember` and `rememberSaveable`?

A: - `remember`: Survives recomposition. - `rememberSaveable`: Survives
configuration changes like rotation.

### Q: What is Unidirectional Data Flow (UDF)?

A: State flows down to UI, and events flow up to ViewModel.

------------------------------------------------------------------------

## 4. Architecture (MVVM + Clean)

### Q: Explain MVVM.

A: UI observes ViewModel. ViewModel holds UI state and calls Repository.
Repository provides data from API/DB.

### Q: What is Clean Architecture?

A: It separates code into Presentation, Domain, and Data layers to
improve testability and maintainability.

### Q: What is a Repository?

A: Repository is a single source of truth for data. It decides whether
to load from API, DB, or cache.

### Q: What is UI State?

A: UI State represents screen state like Loading, Success, Error using
sealed classes.

------------------------------------------------------------------------

## 5. Dependency Injection (Hilt)

### Q: Why use Dependency Injection?

A: For better testability, loose coupling, and easier maintenance.

### Q: What is Hilt?

A: Hilt is Android's recommended DI library built on top of Dagger.

### Q: What is `@HiltViewModel`?

A: It tells Hilt how to provide dependencies to a ViewModel.

------------------------------------------------------------------------

## 6. Networking & Storage

### Q: What is Retrofit?

A: Retrofit is a type-safe HTTP client for Android used for API calls.

### Q: What is Room?

A: Room is an ORM library for SQLite that provides compile-time query
checking.

### Q: What is DataStore?

A: DataStore is a modern replacement for SharedPreferences for storing
small data.

------------------------------------------------------------------------

## 7. Performance

### Q: What causes ANR?

A: Blocking the main thread with long operations like network or heavy
computation.

### Q: How to avoid unnecessary recompositions in Compose?

A: Use `remember`, avoid creating new objects in composables, and use
stable state.

------------------------------------------------------------------------

## 8. Testing

### Q: What should you unit test?

A: ViewModels, UseCases, and business logic.

### Q: Why use fake repositories in tests?

A: To test logic without depending on real API or database.

------------------------------------------------------------------------

## 9. Senior-Level Questions

### Q: How do you design a screen in Compose?

A: UI observes StateFlow from ViewModel, displays state, and sends
events back to ViewModel.

### Q: Coroutines vs Threads?

A: Threads are heavy and blocking, coroutines are lightweight and
non-blocking.

### Q: How do you handle errors in app?

A: Map API errors to UI state and show proper error messages or retry
options.

------------------------------------------------------------------------

## Final Tip

Revise this README, explain concepts in simple words, and relate answers
to your real project experience.



# Senior Android Developer Interview README (6+ Years Experience)

Kotlin • Coroutines • Flow • Jetpack Compose • Architecture •
Performance • Testing • Build • System Design

This file contains **advanced interview Q&A** for Senior / Lead Android
roles.

------------------------------------------------------------------------

## 1. Advanced Kotlin

### Q: What is inline function and why is it used?

A: Inline functions copy the function body at call site, reducing object
allocations for lambdas and improving performance, especially in
higher-order functions.

### Q: What is reified type?

A: Reified allows access to generic type at runtime inside inline
functions, avoiding passing Class`<T>`{=html} manually.

### Q: What is delegation (`by`) in Kotlin?

A: Delegation allows a class to delegate implementation of an interface
or property to another object, improving composition over inheritance.

### Q: Explain immutability in Kotlin and why it matters.

A: Immutability means objects cannot change after creation. It reduces
bugs, makes concurrency safer, and works well with state-driven UI like
Compose.

### Q: Difference between `==` and `===`?

A: - `==` checks structural equality (calls equals()) - `===` checks
referential equality (same object in memory)

------------------------------------------------------------------------

## 2. Coroutines & Flow (Advanced)

### Q: What is structured concurrency?

A: It ensures coroutines are launched in a scope and are cancelled
together, preventing memory leaks and uncontrolled background work.

### Q: Difference between `coroutineScope` and `supervisorScope`?

A: - `coroutineScope`: If one child fails, all are cancelled. -
`supervisorScope`: One child failure does not cancel others.

### Q: How do you handle exceptions in coroutines?

A: Using try/catch, CoroutineExceptionHandler, and proper scope
hierarchy. For async, exceptions are thrown on await().

### Q: Cold Flow vs Hot Flow?

A: - Cold Flow: Starts emitting when collected (Flow). - Hot Flow: Emits
regardless of collectors (StateFlow, SharedFlow).

### Q: When to use SharedFlow vs Channel?

A: SharedFlow for multiple subscribers and UI events, Channel for
one-time communication between coroutines.

### Q: What is backpressure and how Flow handles it?

A: Backpressure happens when producer is faster than consumer. Flow
handles it using suspension and operators like buffer, conflate,
collectLatest.

------------------------------------------------------------------------

## 3. Jetpack Compose (Advanced)

### Q: What is recomposition and how do you control it?

A: Recomposition is re-running composables when state changes. Control
it using remember, derivedStateOf, stable parameters, and avoiding
unnecessary object creation.

### Q: What is Snapshot system in Compose?

A: Snapshot system tracks state reads/writes and triggers recomposition
only where needed.

### Q: Difference between `SideEffect`, `LaunchedEffect`, `DisposableEffect`?

A: - SideEffect: Runs after every successful recomposition. -
LaunchedEffect: Launches coroutine tied to composition. -
DisposableEffect: Used for setup/cleanup like listeners.

### Q: What is state hoisting and why is it important?

A: Moving state to parent composable makes UI reusable, testable, and
follows unidirectional data flow.

### Q: How do you handle one-time events in Compose?

A: Using SharedFlow, Channel, or event wrappers collected inside
LaunchedEffect.

### Q: How do you optimize LazyColumn performance?

A: Use key, avoid heavy composables, use stable data, and avoid
recomposing entire list on small changes.

------------------------------------------------------------------------

## 4. Architecture & System Design

### Q: How do you design a scalable Android app?

A: Use Clean Architecture, modularization, clear separation of concerns,
DI, and state-driven UI.

### Q: Where should business logic live?

A: In UseCases or domain layer, not in ViewModel or UI.

### Q: How do you manage complex UI states?

A: Using sealed classes or data classes representing full UI state,
driven by StateFlow.

### Q: What is Single Source of Truth?

A: One authoritative data source (usually DB or repository) that UI
observes.

### Q: How do you handle offline-first apps?

A: Use Room as source of truth, sync with API, show cached data, update
in background.

------------------------------------------------------------------------

## 5. Dependency Injection (Hilt / Dagger)

### Q: Difference between @Binds and @Provides?

A: - @Binds: For interface to implementation binding, no object creation
logic. - @Provides: For object creation logic.

### Q: What problems does DI solve?

A: Reduces coupling, improves testability, easier replacement of
implementations.

### Q: How does Hilt manage scopes?

A: Using predefined scopes like Singleton, ViewModelScoped,
ActivityRetainedScoped to control object lifetime.

------------------------------------------------------------------------

## 6. Networking, Caching & Data

### Q: How do you design a caching strategy?

A: Repository decides source: DB first, then API, update DB, UI observes
DB.

### Q: How do you handle API errors properly?

A: Map network errors to domain errors, then to UI states with
user-friendly messages.

### Q: DTO vs Domain vs UI models?

A: - DTO: API/DB models - Domain: Business models - UI: Presentation
models

------------------------------------------------------------------------

## 7. Performance & Memory

### Q: Common causes of memory leaks?

A: Holding Activity/Context in static objects, long-lived coroutines,
listeners not removed.

### Q: How do you detect memory leaks?

A: Using LeakCanary and Android Studio profiler.

### Q: How do you avoid ANR?

A: Never block main thread, use coroutines, move heavy work to
background threads.

### Q: How do you improve app startup time?

A: Lazy initialization, defer heavy work, optimize Application class,
baseline profiles.

------------------------------------------------------------------------

## 8. Testing Strategy

### Q: What types of tests do you write?

A: Unit tests (ViewModel, UseCase), Integration tests (Repository), UI
tests (Compose/UI).

### Q: How do you test coroutines?

A: Using runTest, TestDispatcher, and controlling virtual time.

### Q: How do you test ViewModel with Flow?

A: Collect Flow in test, assert emitted states in order.

------------------------------------------------------------------------

## 9. Build System & CI/CD

### Q: What are build variants and flavors?

A: Variants combine build types (debug/release) with flavors (dev/prod)
for different environments.

### Q: What is R8/Proguard?

A: Tool for code shrinking, obfuscation, and optimization in release
builds.

### Q: How do you manage multiple environments?

A: Using product flavors, different base URLs, and config files.

------------------------------------------------------------------------

## 10. Senior / Lead Level Questions

### Q: How do you review code?

A: Check architecture, readability, performance, testability, and edge
cases.

### Q: How do you mentor junior developers?

A: Through code reviews, pair programming, clear guidelines, and design
discussions.

### Q: How do you handle technical debt?

A: Prioritize, refactor gradually, add tests, and align with product
goals.

### Q: How do you make architectural decisions?

A: Based on scalability, team skill, maintenance cost, and business
requirements.

------------------------------------------------------------------------

## Final Advice

Always answer with: - Real project examples - Trade-offs - Why you chose
a solution - How it scales and how it's tested

# Addendum: 50 More Advanced Q&A (Senior Android)

## Kotlin & Language (1--10)

1)  Q: What is a value class? A: A value class (inline class) wraps a
    single value without object allocation at runtime, improving
    performance while keeping type safety.

2)  Q: When do you use tailrec? A: For tail-recursive functions to let
    the compiler optimize recursion into a loop and avoid stack
    overflow.

3)  Q: What is contract in Kotlin? A: Contracts provide compiler hints
    about function behavior (e.g., returns implies condition) to improve
    smart casts and analysis.

4)  Q: Difference between List and MutableList? A: List is read-only
    view; MutableList allows modification. Prefer immutable views for
    safety.

5)  Q: What is SAM conversion? A: Kotlin can convert lambdas to
    single-abstract-method interfaces automatically.

6)  Q: What is operator overloading? A: Defining functions like plus(),
    get(), set() to use operators (+, \[\], etc.) with custom types.

7)  Q: What are type aliases? A: Alternative names for types to improve
    readability without creating new types.

8)  Q: What is lateinit pitfall? A: Access before initialization throws
    exception; not for primitives; watch lifecycle leaks.

9)  Q: When to use sequence? A: For large collections to enable lazy
    evaluation and reduce intermediate allocations.

10) Q: What is copy-on-write with data classes? A: Using copy() to
    create modified immutable instances, common for UI state updates.

## Coroutines & Flow (11--20)

11) Q: What is Dispatchers.Unconfined? A: Starts in caller thread and
    resumes in the suspending function's thread; rarely used in
    production.

12) Q: Difference between withContext and launch? A: withContext
    switches context and returns result; launch starts a new coroutine
    job.

13) Q: What is flowOn? A: Changes the upstream execution context of a
    Flow.

14) Q: What is shareIn/stateIn? A: Operators to convert cold Flow into
    hot SharedFlow/StateFlow within a scope.

15) Q: When to use collectLatest? A: When only the latest value matters
    and previous work should be cancelled (e.g., search).

16) Q: What is buffer vs conflate? A: buffer stores values; conflate
    drops intermediate values keeping latest.

17) Q: How do you cancel a Flow? A: Cancel the collecting coroutine or
    the scope; Flow cooperates with cancellation.

18) Q: What is retryWhen? A: Operator to retry Flow based on error and
    attempt count.

19) Q: How to combine multiple Flows? A: Use combine, zip, or merge
    depending on synchronization needs.

20) Q: What is structured concurrency benefit? A: Predictable lifecycle,
    automatic cancellation, and no leaked work.

## Jetpack Compose (21--30)

21) Q: What is rememberUpdatedState? A: Keeps latest value without
    restarting effects that depend on it.

22) Q: What is CompositionLocal? A: A way to implicitly pass data down
    the tree (e.g., theme, spacing).

23) Q: Difference between Box and ConstraintLayout? A: Box is simple
    stacking; ConstraintLayout handles complex relationships.

24) Q: What is SubcomposeLayout? A: Allows measuring one composable
    based on another's size (advanced layouts).

25) Q: How do you animate state changes? A: Use animate\*AsState,
    updateTransition, or Animatable.

26) Q: What is snapshotFlow? A: Converts Compose state reads into a Flow
    for side-effects.

27) Q: How do you handle large lists efficiently? A: LazyColumn with
    keys, item content types, and stable data.

28) Q: What is rememberSaveable limitation? A: Only saves types
    supported by Bundle or with a custom Saver.

29) Q: How do you debug recomposition? A: Use Layout Inspector,
    Recompose Highlighter, or logging with side-effects.

30) Q: What is UI vs state separation? A: UI is stateless and driven by
    state passed from ViewModel.

## Architecture & DI (31--40)

31) Q: What is modularization benefit? A: Faster builds, better
    isolation, parallel development, clearer boundaries.

32) Q: What is feature module vs core module? A: Feature holds screen
    logic; core holds shared utilities and contracts.

33) Q: What is hexagonal architecture? A: Ports and adapters pattern
    separating business logic from external systems.

34) Q: How do you version APIs safely? A: Use DTO versioning,
    backward-compatible fields, and migration strategies.

35) Q: What is assisted injection? A: Part of constructor is provided by
    DI, part at runtime (e.g., ViewModel with params).

36) Q: How do you scope repositories? A: Usually Singleton to share
    cache and data sources.

37) Q: What is facade pattern use here? A: Simplifies complex subsystems
    (e.g., data layer behind Repository).

38) Q: How do you handle config changes? A: Keep state in
    ViewModel/StateFlow; UI observes.

39) Q: What is MVI vs MVVM? A: MVI uses single immutable state and
    intents; MVVM allows multiple observable states.

40) Q: How do you avoid God ViewModel? A: Split by use-cases, smaller
    state holders, and compose ViewModels per feature.

## Performance, Build, Testing (41--50)

41) Q: What is baseline profile? A: Precompiled code paths to improve
    startup and runtime performance.

42) Q: What is app startup tracing? A: Measure cold/warm/hot start using
    Android Studio or Firebase Performance.

43) Q: Difference between debug and release performance? A: Release uses
    R8, optimizations, no debug overhead; debug is slower.

44) Q: What is strict mode? A: Tool to detect disk/network on main
    thread and other bad practices.

45) Q: How do you test Compose UI? A: Use compose-test APIs to find
    nodes, perform actions, and assert state.

46) Q: What is TestDispatcher? A: A coroutine dispatcher for controlling
    time and execution in tests.

47) Q: How do you mock time in tests? A: Use TestScope and
    advanceTimeBy/advanceUntilIdle.

48) Q: What is screenshot testing? A: Verifies UI rendering by comparing
    images across runs.

49) Q: How do you keep CI fast? A: Module-level tests, caching, parallel
    jobs, and selective test runs.

50) Q: What metrics matter in production? A: Crash-free users, ANR rate,
    startup time, frame drops, and network errors.


