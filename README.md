# Gradle ReplaceTokens issue
## Prerequisites and softwares versions

* Java 8
* Gradle 6.3 wrapper
* Windows 10

## Reproduce the issue
### Execute the command line 
`.\gradlew.bat clean processResources --no-daemon`

### Result

```cmd
To honour the JVM settings for this build a new JVM will be forked. Please consider using the daemon: https://docs.gradle.org/6.3/userguide/gradle_daemon.html.                        
Daemon will be stopped at the end of the build stopping after processing                                                                                                               
> Task :processResources FAILED                                                                                                                                                        
                                                                                                                                                                                       
FAILURE: Build failed with an exception.                                                                                                                                               
                                                                                                                                                                                       
* What went wrong:                                                                                                                                                                     
Execution failed for task ':processResources'.                                                                                                                                         
> Could not copy file 'C:\dvp\workspace\cbm\gradle_ReplaceTokens_issue\src\main\resources\test.txt' to 'C:\dvp\workspace\cbm\gradle_ReplaceTokens_issue\build\resources\main\test.txt'.
   > org.gradle.api.internal.provider.DefaultProviderFactory cannot be cast to java.lang.String                                                                                        
                                                                                                                                                                                       
* Try:                                                                                                                                                                                 
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.                                   
                                                                                                                                                                                       
* Get more help at https://help.gradle.org                                                                                                                                             
                                                                                                                                                                                       
BUILD FAILED in 10s                                                                                                                                                                    
2 actionable tasks: 2 executed                                                                                                                                                         
```

### Complete stacktrace

`.\gradlew.bat clean processResources --no-daemon --stacktrace`

```cmd
To honour the JVM settings for this build a new JVM will be forked. Please consider using the daemon: https://docs.gradle.org/6.3/userguide/gradle_daemon.html.
Daemon will be stopped at the end of the build stopping after processing
> Task :processResources FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':processResources'.
> Could not copy file 'C:\dvp\workspace\cbm\gradle_ReplaceTokens_issue\src\main\resources\test.txt' to 'C:\dvp\workspace\cbm\gradle_ReplaceTokens_issue\build\resources\main\test.txt'.
   > org.gradle.api.internal.provider.DefaultProviderFactory cannot be cast to java.lang.String

* Try:
Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Exception is:
org.gradle.api.tasks.TaskExecutionException: Execution failed for task ':processResources'.
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.lambda$executeIfValid$1(ExecuteActionsTaskExecuter.java:205)
        at org.gradle.internal.Try$Failure.ifSuccessfulOrElse(Try.java:263)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeIfValid(ExecuteActionsTaskExecuter.java:203)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.execute(ExecuteActionsTaskExecuter.java:184)
        at org.gradle.api.internal.tasks.execution.CleanupStaleOutputsExecuter.execute(CleanupStaleOutputsExecuter.java:114)
        at org.gradle.api.internal.tasks.execution.FinalizePropertiesTaskExecuter.execute(FinalizePropertiesTaskExecuter.java:46)
        at org.gradle.api.internal.tasks.execution.ResolveTaskExecutionModeExecuter.execute(ResolveTaskExecutionModeExecuter.java:62)
        at org.gradle.api.internal.tasks.execution.SkipTaskWithNoActionsExecuter.execute(SkipTaskWithNoActionsExecuter.java:57)
        at org.gradle.api.internal.tasks.execution.SkipOnlyIfTaskExecuter.execute(SkipOnlyIfTaskExecuter.java:56)
        at org.gradle.api.internal.tasks.execution.CatchExceptionTaskExecuter.execute(CatchExceptionTaskExecuter.java:36)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.executeTask(EventFiringTaskExecuter.java:77)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:55)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:52)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$CallableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:416)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$CallableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:406)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$1.execute(DefaultBuildOperationExecutor.java:165)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:250)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:158)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:102)
        at org.gradle.internal.operations.DelegatingBuildOperationExecutor.call(DelegatingBuildOperationExecutor.java:36)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter.execute(EventFiringTaskExecuter.java:52)
        at org.gradle.execution.plan.LocalTaskNodeExecutor.execute(LocalTaskNodeExecutor.java:41)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:372)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:359)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:352)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:338)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.lambda$run$0(DefaultPlanExecutor.java:127)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.execute(DefaultPlanExecutor.java:191)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.executeNextNode(DefaultPlanExecutor.java:182)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.run(DefaultPlanExecutor.java:124)
        at org.gradle.execution.plan.DefaultPlanExecutor.process(DefaultPlanExecutor.java:72)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph.executeWithServices(DefaultTaskExecutionGraph.java:189)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph.execute(DefaultTaskExecutionGraph.java:166)
        at org.gradle.execution.SelectedTaskExecutionAction.execute(SelectedTaskExecutionAction.java:41)
        at org.gradle.execution.DefaultBuildWorkExecutor.execute(DefaultBuildWorkExecutor.java:40)
        at org.gradle.execution.DefaultBuildWorkExecutor.access$000(DefaultBuildWorkExecutor.java:24)
        at org.gradle.execution.DefaultBuildWorkExecutor$1.proceed(DefaultBuildWorkExecutor.java:48)
        at org.gradle.execution.DryRunBuildExecutionAction.execute(DryRunBuildExecutionAction.java:49)
        at org.gradle.execution.DefaultBuildWorkExecutor.execute(DefaultBuildWorkExecutor.java:40)
        at org.gradle.execution.DefaultBuildWorkExecutor.execute(DefaultBuildWorkExecutor.java:33)
        at org.gradle.execution.IncludedBuildLifecycleBuildWorkExecutor.execute(IncludedBuildLifecycleBuildWorkExecutor.java:36)
        at org.gradle.execution.DeprecateUndefinedBuildWorkExecutor.execute(DeprecateUndefinedBuildWorkExecutor.java:42)
        at org.gradle.execution.BuildOperationFiringBuildWorkerExecutor$ExecuteTasks.run(BuildOperationFiringBuildWorkerExecutor.java:57)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:402)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:394)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$1.execute(DefaultBuildOperationExecutor.java:165)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:250)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:158)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:92)
        at org.gradle.internal.operations.DelegatingBuildOperationExecutor.run(DelegatingBuildOperationExecutor.java:31)
        at org.gradle.execution.BuildOperationFiringBuildWorkerExecutor.execute(BuildOperationFiringBuildWorkerExecutor.java:42)
        at org.gradle.initialization.DefaultGradleLauncher.runWork(DefaultGradleLauncher.java:255)
        at org.gradle.initialization.DefaultGradleLauncher.doClassicBuildStages(DefaultGradleLauncher.java:164)
        at org.gradle.initialization.DefaultGradleLauncher.doBuildStages(DefaultGradleLauncher.java:140)
        at org.gradle.initialization.DefaultGradleLauncher.executeTasks(DefaultGradleLauncher.java:120)
        at org.gradle.internal.invocation.GradleBuildController$1.create(GradleBuildController.java:74)
        at org.gradle.internal.invocation.GradleBuildController$1.create(GradleBuildController.java:67)
        at org.gradle.internal.work.DefaultWorkerLeaseService.withLocks(DefaultWorkerLeaseService.java:189)
        at org.gradle.internal.work.StopShieldingWorkerLeaseService.withLocks(StopShieldingWorkerLeaseService.java:40)
        at org.gradle.internal.invocation.GradleBuildController.doBuild(GradleBuildController.java:67)
        at org.gradle.internal.invocation.GradleBuildController.run(GradleBuildController.java:56)
        at org.gradle.tooling.internal.provider.ExecuteBuildActionRunner.run(ExecuteBuildActionRunner.java:31)
        at org.gradle.launcher.exec.ChainingBuildActionRunner.run(ChainingBuildActionRunner.java:35)
        at org.gradle.launcher.exec.BuildOutcomeReportingBuildActionRunner.run(BuildOutcomeReportingBuildActionRunner.java:63)
        at org.gradle.tooling.internal.provider.ValidatingBuildActionRunner.run(ValidatingBuildActionRunner.java:32)
        at org.gradle.launcher.exec.BuildCompletionNotifyingBuildActionRunner.run(BuildCompletionNotifyingBuildActionRunner.java:39)
        at org.gradle.launcher.exec.RunAsBuildOperationBuildActionRunner$3.call(RunAsBuildOperationBuildActionRunner.java:51)
        at org.gradle.launcher.exec.RunAsBuildOperationBuildActionRunner$3.call(RunAsBuildOperationBuildActionRunner.java:45)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$CallableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:416)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$CallableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:406)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$1.execute(DefaultBuildOperationExecutor.java:165)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:250)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:158)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:102)
        at org.gradle.internal.operations.DelegatingBuildOperationExecutor.call(DelegatingBuildOperationExecutor.java:36)
        at org.gradle.launcher.exec.RunAsBuildOperationBuildActionRunner.run(RunAsBuildOperationBuildActionRunner.java:45)
        at org.gradle.launcher.exec.InProcessBuildActionExecuter$1.transform(InProcessBuildActionExecuter.java:50)
        at org.gradle.launcher.exec.InProcessBuildActionExecuter$1.transform(InProcessBuildActionExecuter.java:47)
        at org.gradle.composite.internal.DefaultRootBuildState.run(DefaultRootBuildState.java:80)
        at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:47)
        at org.gradle.launcher.exec.InProcessBuildActionExecuter.execute(InProcessBuildActionExecuter.java:31)
        at org.gradle.launcher.exec.BuildTreeScopeBuildActionExecuter.execute(BuildTreeScopeBuildActionExecuter.java:42)
        at org.gradle.launcher.exec.BuildTreeScopeBuildActionExecuter.execute(BuildTreeScopeBuildActionExecuter.java:28)
        at org.gradle.tooling.internal.provider.ContinuousBuildActionExecuter.execute(ContinuousBuildActionExecuter.java:78)
        at org.gradle.tooling.internal.provider.ContinuousBuildActionExecuter.execute(ContinuousBuildActionExecuter.java:52)
        at org.gradle.tooling.internal.provider.SubscribableBuildActionExecuter.execute(SubscribableBuildActionExecuter.java:60)
        at org.gradle.tooling.internal.provider.SubscribableBuildActionExecuter.execute(SubscribableBuildActionExecuter.java:38)
        at org.gradle.tooling.internal.provider.SessionScopeBuildActionExecuter.execute(SessionScopeBuildActionExecuter.java:68)
        at org.gradle.tooling.internal.provider.SessionScopeBuildActionExecuter.execute(SessionScopeBuildActionExecuter.java:38)
        at org.gradle.tooling.internal.provider.GradleThreadBuildActionExecuter.execute(GradleThreadBuildActionExecuter.java:37)
        at org.gradle.tooling.internal.provider.GradleThreadBuildActionExecuter.execute(GradleThreadBuildActionExecuter.java:26)
        at org.gradle.tooling.internal.provider.ParallelismConfigurationBuildActionExecuter.execute(ParallelismConfigurationBuildActionExecuter.java:43)
        at org.gradle.tooling.internal.provider.ParallelismConfigurationBuildActionExecuter.execute(ParallelismConfigurationBuildActionExecuter.java:29)
        at org.gradle.tooling.internal.provider.StartParamsValidatingActionExecuter.execute(StartParamsValidatingActionExecuter.java:60)
        at org.gradle.tooling.internal.provider.StartParamsValidatingActionExecuter.execute(StartParamsValidatingActionExecuter.java:32)
        at org.gradle.tooling.internal.provider.SessionFailureReportingActionExecuter.execute(SessionFailureReportingActionExecuter.java:55)
        at org.gradle.tooling.internal.provider.SessionFailureReportingActionExecuter.execute(SessionFailureReportingActionExecuter.java:41)
        at org.gradle.tooling.internal.provider.SetupLoggingActionExecuter.execute(SetupLoggingActionExecuter.java:48)
        at org.gradle.tooling.internal.provider.SetupLoggingActionExecuter.execute(SetupLoggingActionExecuter.java:32)
        at org.gradle.launcher.daemon.server.exec.ExecuteBuild.doBuild(ExecuteBuild.java:68)
        at org.gradle.launcher.daemon.server.exec.BuildCommandOnly.execute(BuildCommandOnly.java:37)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.WatchForDisconnection.execute(WatchForDisconnection.java:39)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.ResetDeprecationLogger.execute(ResetDeprecationLogger.java:29)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.RequestStopIfSingleUsedDaemon.execute(RequestStopIfSingleUsedDaemon.java:35)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.ForwardClientInput$2.create(ForwardClientInput.java:78)
        at org.gradle.launcher.daemon.server.exec.ForwardClientInput$2.create(ForwardClientInput.java:75)
        at org.gradle.util.Swapper.swap(Swapper.java:38)
        at org.gradle.launcher.daemon.server.exec.ForwardClientInput.execute(ForwardClientInput.java:75)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.LogAndCheckHealth.execute(LogAndCheckHealth.java:50)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.LogToClient.doBuild(LogToClient.java:63)
        at org.gradle.launcher.daemon.server.exec.BuildCommandOnly.execute(BuildCommandOnly.java:37)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.EstablishBuildEnvironment.doBuild(EstablishBuildEnvironment.java:82)
        at org.gradle.launcher.daemon.server.exec.BuildCommandOnly.execute(BuildCommandOnly.java:37)
        at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
        at org.gradle.launcher.daemon.server.exec.StartBuildOrRespondWithBusy$1.run(StartBuildOrRespondWithBusy.java:52)
        at org.gradle.launcher.daemon.server.DaemonStateCoordinator$1.run(DaemonStateCoordinator.java:297)
        at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:64)
        at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:48)
        at org.gradle.internal.concurrent.ThreadFactoryImpl$ManagedThreadRunnable.run(ThreadFactoryImpl.java:56)
Caused by: org.gradle.api.internal.file.AbstractFileTreeElement$CopyFileElementException: Could not copy file 'C:\dvp\workspace\cbm\gradle_ReplaceTokens_issue\src\main\resources\test.txt' to 'C:\dvp\workspace\cbm\gradle_ReplaceTokens_issue\build\resources\main\test.txt'.
        at org.gradle.api.internal.file.AbstractFileTreeElement.copyTo(AbstractFileTreeElement.java:88)
        at org.gradle.api.internal.file.copy.DefaultFileCopyDetails.copyTo(DefaultFileCopyDetails.java:121)
        at org.gradle.api.internal.file.copy.FileCopyAction$FileCopyDetailsInternalAction.processFile(FileCopyAction.java:49)
        at org.gradle.api.internal.file.copy.NormalizingCopyActionDecorator.lambda$execute$0(NormalizingCopyActionDecorator.java:68)
        at org.gradle.api.internal.file.copy.DuplicateHandlingCopyActionDecorator.lambda$execute$0(DuplicateHandlingCopyActionDecorator.java:66)
        at org.gradle.api.internal.file.copy.CopyFileVisitorImpl.processFile(CopyFileVisitorImpl.java:64)
        at org.gradle.api.internal.file.copy.CopyFileVisitorImpl.visitFile(CopyFileVisitorImpl.java:48)
        at org.gradle.api.internal.file.collections.DefaultDirectoryWalker$PathVisitor.visitFile(DefaultDirectoryWalker.java:115)
        at org.gradle.api.internal.file.collections.DefaultDirectoryWalker$PathVisitor.visitFile(DefaultDirectoryWalker.java:68)
        at org.gradle.api.internal.file.collections.DefaultDirectoryWalker.walkDir(DefaultDirectoryWalker.java:62)
        at org.gradle.api.internal.file.collections.DirectoryFileTree.walkDir(DirectoryFileTree.java:149)
        at org.gradle.api.internal.file.collections.DirectoryFileTree.visitFrom(DirectoryFileTree.java:127)
        at org.gradle.api.internal.file.collections.DirectoryFileTree.visit(DirectoryFileTree.java:112)
        at org.gradle.api.internal.file.collections.FileTreeAdapter.visit(FileTreeAdapter.java:94)
        at org.gradle.api.internal.file.CompositeFileTree.visit(CompositeFileTree.java:101)
        at org.gradle.api.internal.file.copy.CopySpecActionImpl.execute(CopySpecActionImpl.java:40)
        at org.gradle.api.internal.file.copy.CopySpecActionImpl.execute(CopySpecActionImpl.java:24)
        at org.gradle.api.internal.file.copy.DefaultCopySpec$DefaultCopySpecResolver.walk(DefaultCopySpec.java:702)
        at org.gradle.api.internal.file.copy.DefaultCopySpec$DefaultCopySpecResolver.walk(DefaultCopySpec.java:704)
        at org.gradle.api.internal.file.copy.DefaultCopySpec.walk(DefaultCopySpec.java:497)
        at org.gradle.api.internal.file.copy.DelegatingCopySpecInternal.walk(DelegatingCopySpecInternal.java:282)
        at org.gradle.api.internal.file.copy.CopySpecBackedCopyActionProcessingStream.process(CopySpecBackedCopyActionProcessingStream.java:39)
        at org.gradle.api.internal.file.copy.DuplicateHandlingCopyActionDecorator.lambda$execute$1(DuplicateHandlingCopyActionDecorator.java:43)
        at org.gradle.api.internal.file.copy.NormalizingCopyActionDecorator.lambda$execute$1(NormalizingCopyActionDecorator.java:60)
        at org.gradle.api.internal.file.copy.FileCopyAction.execute(FileCopyAction.java:38)
        at org.gradle.api.internal.file.copy.NormalizingCopyActionDecorator.execute(NormalizingCopyActionDecorator.java:59)
        at org.gradle.api.internal.file.copy.DuplicateHandlingCopyActionDecorator.execute(DuplicateHandlingCopyActionDecorator.java:43)
        at org.gradle.api.internal.file.copy.CopyActionExecuter.execute(CopyActionExecuter.java:40)
        at org.gradle.api.tasks.AbstractCopyTask.copy(AbstractCopyTask.java:137)
        at org.gradle.language.jvm.tasks.ProcessResources.copy(ProcessResources.java:33)
        at org.gradle.internal.reflect.JavaMethod.invoke(JavaMethod.java:104)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.doExecute(StandardTaskAction.java:49)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:42)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:28)
        at org.gradle.api.internal.AbstractTask$TaskActionWrapper.execute(AbstractTask.java:727)
        at org.gradle.api.internal.AbstractTask$TaskActionWrapper.execute(AbstractTask.java:694)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$3.run(ExecuteActionsTaskExecuter.java:568)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:402)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:394)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$1.execute(DefaultBuildOperationExecutor.java:165)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:250)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:158)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:92)
        at org.gradle.internal.operations.DelegatingBuildOperationExecutor.run(DelegatingBuildOperationExecutor.java:31)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeAction(ExecuteActionsTaskExecuter.java:553)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeActions(ExecuteActionsTaskExecuter.java:536)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.access$300(ExecuteActionsTaskExecuter.java:109)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution.executeWithPreviousOutputFiles(ExecuteActionsTaskExecuter.java:276)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution.execute(ExecuteActionsTaskExecuter.java:265)
        at org.gradle.internal.execution.steps.ExecuteStep.lambda$execute$1(ExecuteStep.java:33)
        at org.gradle.internal.execution.steps.ExecuteStep.execute(ExecuteStep.java:33)
        at org.gradle.internal.execution.steps.ExecuteStep.execute(ExecuteStep.java:26)
        at org.gradle.internal.execution.steps.CleanupOutputsStep.execute(CleanupOutputsStep.java:67)
        at org.gradle.internal.execution.steps.CleanupOutputsStep.execute(CleanupOutputsStep.java:36)
        at org.gradle.internal.execution.steps.ResolveInputChangesStep.execute(ResolveInputChangesStep.java:49)
        at org.gradle.internal.execution.steps.ResolveInputChangesStep.execute(ResolveInputChangesStep.java:34)
        at org.gradle.internal.execution.steps.CancelExecutionStep.execute(CancelExecutionStep.java:43)
        at org.gradle.internal.execution.steps.TimeoutStep.executeWithoutTimeout(TimeoutStep.java:73)
        at org.gradle.internal.execution.steps.TimeoutStep.execute(TimeoutStep.java:54)
        at org.gradle.internal.execution.steps.CatchExceptionStep.execute(CatchExceptionStep.java:34)
        at org.gradle.internal.execution.steps.CreateOutputsStep.execute(CreateOutputsStep.java:44)
        at org.gradle.internal.execution.steps.SnapshotOutputsStep.execute(SnapshotOutputsStep.java:54)
        at org.gradle.internal.execution.steps.SnapshotOutputsStep.execute(SnapshotOutputsStep.java:38)
        at org.gradle.internal.execution.steps.BroadcastChangingOutputsStep.execute(BroadcastChangingOutputsStep.java:49)
        at org.gradle.internal.execution.steps.CacheStep.executeWithoutCache(CacheStep.java:159)
        at org.gradle.internal.execution.steps.CacheStep.execute(CacheStep.java:72)
        at org.gradle.internal.execution.steps.CacheStep.execute(CacheStep.java:43)
        at org.gradle.internal.execution.steps.StoreExecutionStateStep.execute(StoreExecutionStateStep.java:44)
        at org.gradle.internal.execution.steps.StoreExecutionStateStep.execute(StoreExecutionStateStep.java:33)
        at org.gradle.internal.execution.steps.RecordOutputsStep.execute(RecordOutputsStep.java:38)
        at org.gradle.internal.execution.steps.RecordOutputsStep.execute(RecordOutputsStep.java:24)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.executeBecause(SkipUpToDateStep.java:92)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.lambda$execute$0(SkipUpToDateStep.java:85)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.execute(SkipUpToDateStep.java:55)
        at org.gradle.internal.execution.steps.SkipUpToDateStep.execute(SkipUpToDateStep.java:39)
        at org.gradle.internal.execution.steps.ResolveChangesStep.execute(ResolveChangesStep.java:76)
        at org.gradle.internal.execution.steps.ResolveChangesStep.execute(ResolveChangesStep.java:37)
        at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsFinishedStep.execute(MarkSnapshottingInputsFinishedStep.java:36)
        at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsFinishedStep.execute(MarkSnapshottingInputsFinishedStep.java:26)
        at org.gradle.internal.execution.steps.ResolveCachingStateStep.execute(ResolveCachingStateStep.java:94)
        at org.gradle.internal.execution.steps.ResolveCachingStateStep.execute(ResolveCachingStateStep.java:49)
        at org.gradle.internal.execution.steps.CaptureStateBeforeExecutionStep.execute(CaptureStateBeforeExecutionStep.java:79)
        at org.gradle.internal.execution.steps.CaptureStateBeforeExecutionStep.execute(CaptureStateBeforeExecutionStep.java:53)
        at org.gradle.internal.execution.steps.ValidateStep.execute(ValidateStep.java:74)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.lambda$execute$2(SkipEmptyWorkStep.java:78)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:78)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:34)
        at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsStartedStep.execute(MarkSnapshottingInputsStartedStep.java:39)
        at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:40)
        at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:28)
        at org.gradle.internal.execution.impl.DefaultWorkExecutor.execute(DefaultWorkExecutor.java:33)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeIfValid(ExecuteActionsTaskExecuter.java:192)
        ... 123 more
Caused by: java.lang.ClassCastException: org.gradle.api.internal.provider.DefaultProviderFactory cannot be cast to java.lang.String
        at org.apache.tools.ant.filters.ReplaceTokens.read(ReplaceTokens.java:121)
        at org.apache.tools.ant.filters.BaseFilterReader.read(BaseFilterReader.java:84)
        at org.apache.tools.ant.util.ReaderInputStream.read(ReaderInputStream.java:135)
        at org.apache.commons.io.IOUtils.copyLarge(IOUtils.java:2314)
        at org.apache.commons.io.IOUtils.copy(IOUtils.java:2270)
        at org.apache.commons.io.IOUtils.copyLarge(IOUtils.java:2291)
        at org.gradle.api.internal.file.AbstractFileTreeElement.copyTo(AbstractFileTreeElement.java:66)
        at org.gradle.api.internal.file.copy.DefaultFileCopyDetails.copyTo(DefaultFileCopyDetails.java:112)
        at org.gradle.api.internal.file.AbstractFileTreeElement.copyFile(AbstractFileTreeElement.java:102)
        at org.gradle.api.internal.file.AbstractFileTreeElement.copyTo(AbstractFileTreeElement.java:83)
        ... 214 more


* Get more help at https://help.gradle.org

BUILD FAILED in 13s
2 actionable tasks: 2 executed
```
