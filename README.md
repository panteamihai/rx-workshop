# Reactive Programming with Rx.NET

We're walking the path set forth by Lee Campbell's [Intro to Rx].

## Stopovers

* [Key types]
    * `IObservable<T>` and `IObserver<T>` (and maybe even `ISubject<T>`)
    * `Subject<T>`, `ReplaySubject<T>`, `BehaviorSubject<T>`, `AsyncSubject<T>`
* [Lifetime management]
    * `IDisposable` and its variants
    * The `IDisposable` returned by the `Subscribe` extension methods will dispose itself upon `OnCompleted` or `OnError`. Other implementations won't. Still, you should always capture and dispose of subscriptions yourself when possible.
* [Creating sequences]
    * Introducing `Timestamp` and `TimeInterval` as handy tools for reasoning about streams
    * Creating sequences and the power of the lazily evaluated `Observable.Create`
    * Functional unfolds and the other powerful generation method: `Observable.Generate`
    * Transitioning into observables by switching between domains (from `Task` or `Action`/`Func`)
* [Reducing sequences]
    * Filtering with `Where`
    * Determining `Distinct` elements, and introducing pairwise distinction with `DistinctUntilChanged`
    * `Skip` and `Take`
* [Inspecting sequences]
    * `Any` vs. `All` vs. `Contains`
    * Gracefully handling the empty sequence scenario
    * `ElementAt` and why not to use it
    * Comparing two sequences for equality with `SequenceEqual`
* [Aggregating sequences]
    * Sequence math: `Min`, `Max`, `Sum`, `Average`
    * Functional folds: `First/Last/Single[OrDefault][Async]`
    * Custom aggregations and the relationship between `Aggregate` and `Scan`
    * Partitioning sequences
* [Transforming sequences]
    * Mapping with `Select` and its contactual obligations
    * Casting and materializing
    * `SelectMany`, the powerful `bind function`
    * Visualizing sequences
* [Side effects]
    * Never leak effects out of pipelines, but if you must, use `Do` to emphasize them
* [Advanced error handling]
    * `Catch` vs. `OnErrorResumeNext`, maybe `Retry`
    * `Using` binds the lifetime of a resource to that of a sequence
    * `Finally` no matter what
* [Combining sequences]
    * Combining sequentially requires completion: `Concat`, `Repeat`, `StartWith`
    * Combining concurrently doesn't: `Amb`, `Merge`, `Switch`
    * Pairing is either in sync with the rate of generation: `Zip` & `And/Then/When`, or it isn't: `CombineLatest`
* [Time-shifted sequences]
    * `Buffer`ing: size vs. time triggers
    * Overlapping, rolling or skipped buffering
    * Simple time shifting with `Delay`
    * `Sample` vs. `Throttle`
    * `Timeout` and the beauty of operator composure
* [Temperature]
    * Use `Publish` and `Connect` for taming hotness
    * Use `Publish` and `RefCount` for the added benefit of *the last guy turns off the light*
    * Discover `Multicast` and its power
* [Scheduling]
    * Rx is **single threaded** and **synchronous** by default
    * `SubscribeOn` is for scheduling the subscription code (like for `Observable.Create`)
    * `ObserveOn` is for moving the processing to another thread
    * Advanced scheduling concepts: passing state, cancellation, recursion
    * `ImmediateScheduler` [vs.] `CurrentThreadScheduler`, `EventLoopScheduler` vs. `NewThreadScheduler`
    * `ThreadPoolScheduler`vs. `TaskPoolScheduler`, `DispatcherScheduler`
* [Testing]
    * Virtual time and how to control it: `AdvanceTo` vs. `AdvanceBy`, `Start`
    * Testing pipelines by mocking its schedulers with `TestScheduler`
    * The `ITestableObserver` interface and controlling replay
* [Sequences of coincidence]
    * Generating windows with `Window`
    * Combining windows with `Join` and `GroupJoin`

[Intro to Rx]: <http://introtorx.com/>
[Key types]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/KeyTypes.cs>
[Lifetime management]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/LifetimeManagement.cs>
[Creating sequences]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/CreatingSequences.cs>
[Reducing sequences]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/ReducingSequences.cs>
[Inspecting sequences]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/InspectingSequences.cs>
[Aggregating sequences]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/AggregatingSequences.cs>
[Transforming sequences]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/TransformingSequences.cs>
[Side effects]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/SideEffects.cs>
[Advanced error handling]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/AdvancedErrorHandling.cs>
[Combining sequences]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/CombiningSequences.cs>
[Time-shifted sequences]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/TimeshiftedSequences.cs>
[Temperature]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/Temperature.cs>
[Scheduling]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/Scheduling.cs>
[Testing]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/Testing.cs>
[vs.]: <https://social.msdn.microsoft.com/Forums/en-US/7f75482f-eff2-4938-9491-47fe870989e8/currentthreadscheduler-vs-immediatescheduler?forum=rx>
[Sequences of coincidence]: <https://github.com/panteamihai/workshop-rx/blob/master/RxWorkshop/SequencesOfCoincidence.cs>