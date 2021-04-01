# Sample project for bug with mergeExtDex bug

## Clean your Gradle transforms cache

```
rm -rf $GRADLE_HOME/caches/transforms*
```

## Run Gradle task

```
./gradlew --rerun-tasks --stacktrace app:mergeExtDexDebug app:mergeExtDexDebugAndroidTest
```

## Get a build error

<details>
  <summary>Failed build log</summary>
  
  > Task :app:mergeExtDexDebug FAILED
/Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex: D8: Type androidx.fragment.app.BackStackState$1 is defined multiple times: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex, /Users/a.ershov/.gradle/caches/transforms-3/650e2eda7cbfe2af44679968a796fa3b/transformed/fragment-1.1.0-runtime/classes.dex
com.android.builder.dexing.DexArchiveMergerException: Error while merging dex archives: 
Learn how to resolve the issue at https://developer.android.com/studio/build/dependencies#duplicate_classes.
Type androidx.fragment.app.BackStackState$1 is defined multiple times: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex, /Users/a.ershov/.gradle/caches/transforms-3/650e2eda7cbfe2af44679968a796fa3b/transformed/fragment-1.1.0-runtime/classes.dex
        at com.android.builder.dexing.D8DexArchiveMerger.getExceptionToRethrow(D8DexArchiveMerger.java:132)
        at com.android.builder.dexing.D8DexArchiveMerger.mergeDexArchives(D8DexArchiveMerger.java:119)
        at com.android.build.gradle.internal.transforms.DexMergerTransformCallable.call(DexMergerTransformCallable.java:102)
        at com.android.build.gradle.internal.tasks.DexMergingTaskRunnable.run(DexMergingTask.kt:432)
        at com.android.build.gradle.internal.tasks.Workers$ActionFacade.run(Workers.kt:242)
        at org.gradle.workers.internal.AdapterWorkAction.execute(AdapterWorkAction.java:57)
        at org.gradle.workers.internal.DefaultWorkerServer.execute(DefaultWorkerServer.java:63)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1$1.create(NoIsolationWorkerFactory.java:67)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1$1.create(NoIsolationWorkerFactory.java:63)
        at org.gradle.internal.classloader.ClassLoaderUtils.executeInClassloader(ClassLoaderUtils.java:97)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1.lambda$execute$0(NoIsolationWorkerFactory.java:63)
        at org.gradle.workers.internal.AbstractWorker$1.call(AbstractWorker.java:44)
        at org.gradle.workers.internal.AbstractWorker$1.call(AbstractWorker.java:41)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
        at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
        at org.gradle.workers.internal.AbstractWorker.executeWrappedInBuildOperation(AbstractWorker.java:41)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1.execute(NoIsolationWorkerFactory.java:60)
        at org.gradle.workers.internal.DefaultWorkerExecutor.lambda$submitWork$2(DefaultWorkerExecutor.java:200)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at org.gradle.internal.work.DefaultConditionalExecutionQueue$ExecutionRunner.runExecution(DefaultConditionalExecutionQueue.java:214)
        at org.gradle.internal.work.DefaultConditionalExecutionQueue$ExecutionRunner.runBatch(DefaultConditionalExecutionQueue.java:164)
        at org.gradle.internal.work.DefaultConditionalExecutionQueue$ExecutionRunner.run(DefaultConditionalExecutionQueue.java:131)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:64)
        at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:48)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1130)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:630)
        at org.gradle.internal.concurrent.ThreadFactoryImpl$ManagedThreadRunnable.run(ThreadFactoryImpl.java:56)
        at java.base/java.lang.Thread.run(Thread.java:832)
Caused by: com.android.tools.r8.CompilationFailedException: Compilation failed to complete, origin: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex
        at Version.fakeStackEntry(Version_2.1.86.java:0)
        at com.android.tools.r8.utils.Y.a(SourceFile:78)
        at com.android.tools.r8.D8.run(D8.java:11)
        at com.android.builder.dexing.D8DexArchiveMerger.mergeDexArchives(D8DexArchiveMerger.java:117)
        ... 36 more
Caused by: com.android.tools.r8.utils.b: Type androidx.fragment.app.BackStackState$1 is defined multiple times: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex, /Users/a.ershov/.gradle/caches/transforms-3/650e2eda7cbfe2af44679968a796fa3b/transformed/fragment-1.1.0-runtime/classes.dex
        at com.android.tools.r8.utils.T0.error(SourceFile:1)
        at com.android.tools.r8.utils.T0.a(SourceFile:2)
        at com.android.tools.r8.utils.R0.b(SourceFile:6)
        at com.android.tools.r8.utils.R0.a(SourceFile:24)
        at com.android.tools.r8.utils.R0.a(SourceFile:10)
        at java.base/java.util.concurrent.ConcurrentHashMap.merge(ConcurrentHashMap.java:2056)
        at com.android.tools.r8.utils.R0.a(SourceFile:6)
        at com.android.tools.r8.graph.Q0$c.f(SourceFile:3)
        at com.android.tools.r8.dex.a.a(SourceFile:298)
        at com.android.tools.r8.dex.a.a(SourceFile:226)
        at com.android.tools.r8.D8.d(D8.java:6)
        at com.android.tools.r8.D8.b(D8.java:1)
        at com.android.tools.r8.utils.Y.a(SourceFile:36)
        ... 38 more


FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:mergeExtDexDebug'.
> A failure occurred while executing com.android.build.gradle.internal.tasks.Workers$ActionFacade
   > com.android.builder.dexing.DexArchiveMergerException: Error while merging dex archives: 
     Learn how to resolve the issue at https://developer.android.com/studio/build/dependencies#duplicate_classes.
     Type androidx.fragment.app.BackStackState$1 is defined multiple times: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex, /Users/a.ershov/.gradle/caches/transforms-3/650e2eda7cbfe2af44679968a796fa3b/transformed/fragment-1.1.0-runtime/classes.dex

* Try:
Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Exception is:
org.gradle.api.tasks.TaskExecutionException: Execution failed for task ':app:mergeExtDexDebug'.
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.lambda$executeIfValid$3(ExecuteActionsTaskExecuter.java:186)
        at org.gradle.internal.Try$Failure.ifSuccessfulOrElse(Try.java:268)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeIfValid(ExecuteActionsTaskExecuter.java:184)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.execute(ExecuteActionsTaskExecuter.java:173)
        at org.gradle.api.internal.tasks.execution.CleanupStaleOutputsExecuter.execute(CleanupStaleOutputsExecuter.java:109)
        at org.gradle.api.internal.tasks.execution.FinalizePropertiesTaskExecuter.execute(FinalizePropertiesTaskExecuter.java:46)
        at org.gradle.api.internal.tasks.execution.ResolveTaskExecutionModeExecuter.execute(ResolveTaskExecutionModeExecuter.java:62)
        at org.gradle.api.internal.tasks.execution.SkipTaskWithNoActionsExecuter.execute(SkipTaskWithNoActionsExecuter.java:57)
        at org.gradle.api.internal.tasks.execution.SkipOnlyIfTaskExecuter.execute(SkipOnlyIfTaskExecuter.java:56)
        at org.gradle.api.internal.tasks.execution.CatchExceptionTaskExecuter.execute(CatchExceptionTaskExecuter.java:36)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.executeTask(EventFiringTaskExecuter.java:77)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:55)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:52)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
        at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter.execute(EventFiringTaskExecuter.java:52)
        at org.gradle.execution.plan.LocalTaskNodeExecutor.execute(LocalTaskNodeExecutor.java:41)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:411)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:398)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:391)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:377)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.lambda$run$0(DefaultPlanExecutor.java:127)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.execute(DefaultPlanExecutor.java:191)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.executeNextNode(DefaultPlanExecutor.java:182)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.run(DefaultPlanExecutor.java:124)
        at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:64)
        at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:48)
        at org.gradle.internal.concurrent.ThreadFactoryImpl$ManagedThreadRunnable.run(ThreadFactoryImpl.java:56)
Caused by: org.gradle.workers.internal.DefaultWorkerExecutor$WorkExecutionException: A failure occurred while executing com.android.build.gradle.internal.tasks.Workers$ActionFacade
        at org.gradle.workers.internal.DefaultWorkerExecutor$WorkItemExecution.waitForCompletion(DefaultWorkerExecutor.java:336)
        at org.gradle.internal.work.DefaultAsyncWorkTracker.waitForItemsAndGatherFailures(DefaultAsyncWorkTracker.java:142)
        at org.gradle.internal.work.DefaultAsyncWorkTracker.waitForItemsAndGatherFailures(DefaultAsyncWorkTracker.java:94)
        at org.gradle.internal.work.DefaultAsyncWorkTracker.waitForAll(DefaultAsyncWorkTracker.java:80)
        at org.gradle.internal.work.DefaultAsyncWorkTracker.waitForCompletion(DefaultAsyncWorkTracker.java:68)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$2.run(ExecuteActionsTaskExecuter.java:502)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$1.execute(DefaultBuildOperationRunner.java:29)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$1.execute(DefaultBuildOperationRunner.java:26)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.run(DefaultBuildOperationRunner.java:56)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$run$1(DefaultBuildOperationExecutor.java:71)
        at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.runWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:45)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:71)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeAction(ExecuteActionsTaskExecuter.java:479)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeActions(ExecuteActionsTaskExecuter.java:462)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.access$400(ExecuteActionsTaskExecuter.java:105)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution.executeWithPreviousOutputFiles(ExecuteActionsTaskExecuter.java:273)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution.execute(ExecuteActionsTaskExecuter.java:251)
        at org.gradle.internal.execution.steps.ExecuteStep.lambda$executeOperation$0(ExecuteStep.java:65)
        at org.gradle.internal.execution.steps.ExecuteStep.executeOperation(ExecuteStep.java:65)
        at org.gradle.internal.execution.steps.ExecuteStep.access$000(ExecuteStep.java:34)
        at org.gradle.internal.execution.steps.ExecuteStep$1.call(ExecuteStep.java:47)
        at org.gradle.internal.execution.steps.ExecuteStep$1.call(ExecuteStep.java:44)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
        at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
        at org.gradle.internal.execution.steps.ExecuteStep.execute(ExecuteStep.java:44)
        at org.gradle.internal.execution.steps.ExecuteStep.execute(ExecuteStep.java:34)
        at org.gradle.internal.execution.steps.RemovePreviousOutputsStep.execute(RemovePreviousOutputsStep.java:72)
        at org.gradle.internal.execution.steps.RemovePreviousOutputsStep.execute(RemovePreviousOutputsStep.java:42)
        at org.gradle.internal.execution.steps.ResolveInputChangesStep.execute(ResolveInputChangesStep.java:53)
        at org.gradle.internal.execution.steps.ResolveInputChangesStep.execute(ResolveInputChangesStep.java:39)
        at org.gradle.internal.execution.steps.CancelExecutionStep.execute(CancelExecutionStep.java:44)
        at org.gradle.internal.execution.steps.TimeoutStep.executeWithoutTimeout(TimeoutStep.java:77)
        at org.gradle.internal.execution.steps.TimeoutStep.execute(TimeoutStep.java:58)
        at org.gradle.internal.execution.steps.CreateOutputsStep.execute(CreateOutputsStep.java:54)
        at org.gradle.internal.execution.steps.CreateOutputsStep.execute(CreateOutputsStep.java:32)
        at org.gradle.internal.execution.steps.CaptureStateAfterExecutionStep.execute(CaptureStateAfterExecutionStep.java:57)
        at org.gradle.internal.execution.steps.CaptureStateAfterExecutionStep.execute(CaptureStateAfterExecutionStep.java:38)
        at org.gradle.internal.execution.steps.BroadcastChangingOutputsStep.execute(BroadcastChangingOutputsStep.java:63)
        at org.gradle.internal.execution.steps.BroadcastChangingOutputsStep.execute(BroadcastChangingOutputsStep.java:30)
        at org.gradle.internal.execution.steps.BuildCacheStep.executeWithoutCache(BuildCacheStep.java:176)
        at org.gradle.internal.execution.steps.BuildCacheStep.execute(BuildCacheStep.java:76)
        at org.gradle.internal.execution.steps.BuildCacheStep.execute(BuildCacheStep.java:47)
        at org.gradle.internal.execution.steps.StoreExecutionStateStep.execute(StoreExecutionStateStep.java:43)
        at org.gradle.internal.execution.steps.StoreExecutionStateStep.execute(StoreExecutionStateStep.java:32)
        at org.gradle.internal.execution.steps.RecordOutputsStep.execute(RecordOutputsStep.java:39)
        at org.gradle.internal.execution.steps.RecordOutputsStep.execute(RecordOutputsStep.java:25)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.executeBecause(SkipUpToDateStep.java:102)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.lambda$execute$0(SkipUpToDateStep.java:95)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.execute(SkipUpToDateStep.java:55)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.execute(SkipUpToDateStep.java:39)
        at org.gradle.internal.execution.steps.ResolveChangesStep.execute(ResolveChangesStep.java:83)
        at org.gradle.internal.execution.steps.ResolveChangesStep.execute(ResolveChangesStep.java:44)
        at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsFinishedStep.execute(MarkSnapshottingInputsFinishedStep.java:37)
        at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsFinishedStep.execute(MarkSnapshottingInputsFinishedStep.java:27)
        at org.gradle.internal.execution.steps.ResolveCachingStateStep.execute(ResolveCachingStateStep.java:96)
        at org.gradle.internal.execution.steps.ResolveCachingStateStep.execute(ResolveCachingStateStep.java:52)
        at org.gradle.internal.execution.steps.CaptureStateBeforeExecutionStep.execute(CaptureStateBeforeExecutionStep.java:83)
        at org.gradle.internal.execution.steps.CaptureStateBeforeExecutionStep.execute(CaptureStateBeforeExecutionStep.java:54)
        at org.gradle.internal.execution.steps.ValidateStep.execute(ValidateStep.java:74)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.lambda$execute$2(SkipEmptyWorkStep.java:88)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:88)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:34)
        at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsStartedStep.execute(MarkSnapshottingInputsStartedStep.java:38)
        at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:46)
        at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:34)
        at org.gradle.internal.execution.steps.AssignWorkspaceStep.lambda$execute$0(AssignWorkspaceStep.java:43)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution$3.withWorkspace(ExecuteActionsTaskExecuter.java:286)
        at org.gradle.internal.execution.steps.AssignWorkspaceStep.execute(AssignWorkspaceStep.java:43)
        at org.gradle.internal.execution.steps.AssignWorkspaceStep.execute(AssignWorkspaceStep.java:33)
        at org.gradle.internal.execution.steps.IdentityCacheStep.execute(IdentityCacheStep.java:40)
        at org.gradle.internal.execution.steps.IdentityCacheStep.execute(IdentityCacheStep.java:30)
        at org.gradle.internal.execution.steps.IdentifyStep.execute(IdentifyStep.java:54)
        at org.gradle.internal.execution.steps.IdentifyStep.execute(IdentifyStep.java:40)
        at org.gradle.internal.execution.impl.DefaultExecutionEngine.rebuild(DefaultExecutionEngine.java:46)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.lambda$executeIfValid$0(ExecuteActionsTaskExecuter.java:182)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeIfValid(ExecuteActionsTaskExecuter.java:182)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.execute(ExecuteActionsTaskExecuter.java:173)
        at org.gradle.api.internal.tasks.execution.CleanupStaleOutputsExecuter.execute(CleanupStaleOutputsExecuter.java:109)
        at org.gradle.api.internal.tasks.execution.FinalizePropertiesTaskExecuter.execute(FinalizePropertiesTaskExecuter.java:46)
        at org.gradle.api.internal.tasks.execution.ResolveTaskExecutionModeExecuter.execute(ResolveTaskExecutionModeExecuter.java:62)
        at org.gradle.api.internal.tasks.execution.SkipTaskWithNoActionsExecuter.execute(SkipTaskWithNoActionsExecuter.java:57)
        at org.gradle.api.internal.tasks.execution.SkipOnlyIfTaskExecuter.execute(SkipOnlyIfTaskExecuter.java:56)
        at org.gradle.api.internal.tasks.execution.CatchExceptionTaskExecuter.execute(CatchExceptionTaskExecuter.java:36)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.executeTask(EventFiringTaskExecuter.java:77)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:55)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:52)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
        at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter.execute(EventFiringTaskExecuter.java:52)
        at org.gradle.execution.plan.LocalTaskNodeExecutor.execute(LocalTaskNodeExecutor.java:41)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:411)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:398)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:391)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:377)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.lambda$run$0(DefaultPlanExecutor.java:127)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.execute(DefaultPlanExecutor.java:191)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.executeNextNode(DefaultPlanExecutor.java:182)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.run(DefaultPlanExecutor.java:124)
        at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:64)
        at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:48)
        at org.gradle.internal.concurrent.ThreadFactoryImpl$ManagedThreadRunnable.run(ThreadFactoryImpl.java:56)
Caused by: com.android.build.api.transform.TransformException: com.android.builder.dexing.DexArchiveMergerException: Error while merging dex archives: 
Learn how to resolve the issue at https://developer.android.com/studio/build/dependencies#duplicate_classes.
Type androidx.fragment.app.BackStackState$1 is defined multiple times: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex, /Users/a.ershov/.gradle/caches/transforms-3/650e2eda7cbfe2af44679968a796fa3b/transformed/fragment-1.1.0-runtime/classes.dex
        at com.android.build.gradle.internal.tasks.DexMergingTaskRunnable.run(DexMergingTask.kt:459)
        at com.android.build.gradle.internal.tasks.Workers$ActionFacade.run(Workers.kt:242)
        at org.gradle.workers.internal.AdapterWorkAction.execute(AdapterWorkAction.java:57)
        at org.gradle.workers.internal.DefaultWorkerServer.execute(DefaultWorkerServer.java:63)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1$1.create(NoIsolationWorkerFactory.java:67)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1$1.create(NoIsolationWorkerFactory.java:63)
        at org.gradle.internal.classloader.ClassLoaderUtils.executeInClassloader(ClassLoaderUtils.java:97)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1.lambda$execute$0(NoIsolationWorkerFactory.java:63)
        at org.gradle.workers.internal.AbstractWorker$1.call(AbstractWorker.java:44)
        at org.gradle.workers.internal.AbstractWorker$1.call(AbstractWorker.java:41)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
        at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
        at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
        at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
        at org.gradle.workers.internal.AbstractWorker.executeWrappedInBuildOperation(AbstractWorker.java:41)
        at org.gradle.workers.internal.NoIsolationWorkerFactory$1.execute(NoIsolationWorkerFactory.java:60)
        at org.gradle.workers.internal.DefaultWorkerExecutor.lambda$submitWork$2(DefaultWorkerExecutor.java:200)
        at org.gradle.internal.work.DefaultConditionalExecutionQueue$ExecutionRunner.runExecution(DefaultConditionalExecutionQueue.java:214)
        at org.gradle.internal.work.DefaultConditionalExecutionQueue$ExecutionRunner.runBatch(DefaultConditionalExecutionQueue.java:164)
        at org.gradle.internal.work.DefaultConditionalExecutionQueue$ExecutionRunner.run(DefaultConditionalExecutionQueue.java:131)
        ... 3 more
Caused by: com.android.builder.dexing.DexArchiveMergerException: Error while merging dex archives: 
Learn how to resolve the issue at https://developer.android.com/studio/build/dependencies#duplicate_classes.
Type androidx.fragment.app.BackStackState$1 is defined multiple times: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex, /Users/a.ershov/.gradle/caches/transforms-3/650e2eda7cbfe2af44679968a796fa3b/transformed/fragment-1.1.0-runtime/classes.dex
        at com.android.builder.dexing.D8DexArchiveMerger.getExceptionToRethrow(D8DexArchiveMerger.java:132)
        at com.android.builder.dexing.D8DexArchiveMerger.mergeDexArchives(D8DexArchiveMerger.java:119)
        at com.android.build.gradle.internal.transforms.DexMergerTransformCallable.call(DexMergerTransformCallable.java:102)
        at com.android.build.gradle.internal.tasks.DexMergingTaskRunnable.run(DexMergingTask.kt:432)
        ... 28 more
Caused by: com.android.tools.r8.CompilationFailedException: Compilation failed to complete, origin: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex
        at Version.fakeStackEntry(Version_2.1.86.java:0)
        at com.android.tools.r8.utils.Y.a(SourceFile:78)
        at com.android.tools.r8.D8.run(D8.java:11)
        at com.android.builder.dexing.D8DexArchiveMerger.mergeDexArchives(D8DexArchiveMerger.java:117)
        ... 30 more
Caused by: com.android.tools.r8.utils.b: Type androidx.fragment.app.BackStackState$1 is defined multiple times: /Users/a.ershov/.gradle/caches/transforms-3/b54d40150be364a8a5e9aa0f6c1c6ee2/transformed/fragment-1.1.0-runtime/classes.dex, /Users/a.ershov/.gradle/caches/transforms-3/650e2eda7cbfe2af44679968a796fa3b/transformed/fragment-1.1.0-runtime/classes.dex
        at com.android.tools.r8.utils.T0.error(SourceFile:1)
        at com.android.tools.r8.utils.T0.a(SourceFile:2)
        at com.android.tools.r8.utils.R0.b(SourceFile:6)
        at com.android.tools.r8.utils.R0.a(SourceFile:24)
        at com.android.tools.r8.utils.R0.a(SourceFile:10)
        at com.android.tools.r8.utils.R0.a(SourceFile:6)
        at com.android.tools.r8.graph.Q0$c.f(SourceFile:3)
        at com.android.tools.r8.dex.a.a(SourceFile:298)
        at com.android.tools.r8.dex.a.a(SourceFile:226)
        at com.android.tools.r8.D8.d(D8.java:6)
        at com.android.tools.r8.D8.b(D8.java:1)
        at com.android.tools.r8.utils.Y.a(SourceFile:36)
        ... 32 more


* Get more help at https://help.gradle.org

BUILD FAILED in 8s
6 actionable tasks: 6 executed

Publishing build scan...
https://gradle.com/s/c4c4rwjlohe4i
  
</details>

## See `app/build.gradle` for details
