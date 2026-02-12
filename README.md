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
