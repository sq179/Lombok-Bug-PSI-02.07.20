# Intellij IDEA Lombok bug 02.07.20

### How to reproduce:

Open the project source code in the IDEA-EAP 2020.2, then uncomment 
line above lombok in ```com.sq179.reproduce.SampleDataClass``` and you get something like:

```
com.intellij.psi.PsiInvalidElementAccessException: Element: class de.plushnikov.intellij.plugin.psi.LombokLightMethodBuilder #JAVA  because: psi is outdated
invalidated at: no info
	at com.intellij.psi.util.PsiUtilCore.ensureValid(PsiUtilCore.java:477)
	at com.intellij.psi.impl.PsiClassImplUtil.lambda$createMembersMap$4(PsiClassImplUtil.java:346)
	at com.intellij.util.containers.ConcurrentFactoryMap$2.create(ConcurrentFactoryMap.java:174)
	at com.intellij.util.containers.ConcurrentFactoryMap.get(ConcurrentFactoryMap.java:40)
	at com.intellij.psi.impl.PsiClassImplUtil$MembersMap.get(PsiClassImplUtil.java:326)
	at com.intellij.psi.impl.PsiClassImplUtil$MembersMap.access$000(PsiClassImplUtil.java:318)
	at com.intellij.psi.impl.PsiClassImplUtil.getMap(PsiClassImplUtil.java:175)
	at com.intellij.psi.impl.PsiClassImplUtil.getAllByMap(PsiClassImplUtil.java:166)
	at com.intellij.psi.impl.PsiClassImplUtil.getAllMethods(PsiClassImplUtil.java:58)
	at com.intellij.psi.impl.source.PsiClassImpl.getAllMethods(PsiClassImpl.java:335)
	at com.intellij.execution.junit.JUnitUtil.lambda$isJUnit5TestClass$1(JUnitUtil.java:308)
	at com.intellij.psi.util.CachedValuesManager$1.compute(CachedValuesManager.java:153)
	at com.intellij.psi.impl.PsiCachedValueImpl.doCompute(PsiCachedValueImpl.java:54)
	at com.intellij.util.CachedValueBase.lambda$getValueWithLock$1(CachedValueBase.java:235)
	at com.intellij.openapi.util.RecursionManager$1.doPreventingRecursion(RecursionManager.java:112)
	at com.intellij.openapi.util.RecursionManager.doPreventingRecursion(RecursionManager.java:71)
	at com.intellij.util.CachedValueBase.getValueWithLock(CachedValueBase.java:236)
	at com.intellij.psi.impl.PsiCachedValueImpl.getValue(PsiCachedValueImpl.java:43)
	at com.intellij.util.CachedValuesManagerImpl.getCachedValue(CachedValuesManagerImpl.java:76)
	at com.intellij.psi.util.CachedValuesManager.getCachedValue(CachedValuesManager.java:150)
	at com.intellij.psi.util.CachedValuesManager.getCachedValue(CachedValuesManager.java:120)
	at com.intellij.execution.junit.JUnitUtil.isJUnit5TestClass(JUnitUtil.java:306)
	at com.intellij.execution.junit.JUnit5Framework.isTestClass(JUnit5Framework.java:56)
	at com.intellij.testIntegration.JavaTestFramework.isTestClass(JavaTestFramework.java:55)
	at com.intellij.codeInsight.TestFrameworks.computeFramework(TestFrameworks.java:88)
	at com.intellij.codeInsight.TestFrameworks.lambda$detectFramework$0(TestFrameworks.java:59)
	at com.intellij.psi.util.CachedValuesManager$1.compute(CachedValuesManager.java:153)
	at com.intellij.psi.impl.PsiCachedValueImpl.doCompute(PsiCachedValueImpl.java:54)
	at com.intellij.util.CachedValueBase.lambda$getValueWithLock$1(CachedValueBase.java:235)
	at com.intellij.openapi.util.RecursionManager$1.doPreventingRecursion(RecursionManager.java:112)
	at com.intellij.openapi.util.RecursionManager.doPreventingRecursion(RecursionManager.java:71)
	at com.intellij.util.CachedValueBase.getValueWithLock(CachedValueBase.java:236)
	at com.intellij.psi.impl.PsiCachedValueImpl.getValue(PsiCachedValueImpl.java:43)
	at com.intellij.util.CachedValuesManagerImpl.getCachedValue(CachedValuesManagerImpl.java:76)
	at com.intellij.psi.util.CachedValuesManager.getCachedValue(CachedValuesManager.java:150)
	at com.intellij.psi.util.CachedValuesManager.getCachedValue(CachedValuesManager.java:120)
	at com.intellij.codeInsight.TestFrameworks.detectFramework(TestFrameworks.java:58)
	at com.intellij.testIntegration.createTest.CreateTestAction.isAvailableForElement(CreateTestAction.java:86)
	at com.intellij.testIntegration.createTest.CreateTestAction.isAvailable(CreateTestAction.java:54)
	at com.intellij.codeInsight.intention.impl.ShowIntentionActionsHandler.availableFor(ShowIntentionActionsHandler.java:153)
	at com.intellij.codeInsight.daemon.impl.ShowIntentionsPass.lambda$getActionsToShow$1(ShowIntentionsPass.java:322)
	at com.intellij.codeInsight.intention.impl.ShowIntentionActionsHandler.chooseBetweenHostAndInjected(ShowIntentionActionsHandler.java:190)
	at com.intellij.codeInsight.daemon.impl.ShowIntentionsPass.getActionsToShow(ShowIntentionsPass.java:321)
	at com.intellij.codeInsight.daemon.impl.ShowIntentionsPass.doCollectInformation(ShowIntentionsPass.java:226)
	at com.intellij.codeHighlighting.TextEditorHighlightingPass.collectInformation(TextEditorHighlightingPass.java:54)
	at com.intellij.codeInsight.daemon.impl.PassExecutorService$ScheduledPass.lambda$doRun$1(PassExecutorService.java:399)
	at com.intellij.openapi.application.impl.ApplicationImpl.tryRunReadAction(ApplicationImpl.java:1110)
	at com.intellij.codeInsight.daemon.impl.PassExecutorService$ScheduledPass.lambda$doRun$2(PassExecutorService.java:392)
	at com.intellij.openapi.progress.impl.CoreProgressManager.registerIndicatorAndRun(CoreProgressManager.java:629)
	at com.intellij.openapi.progress.impl.CoreProgressManager.executeProcessUnderProgress(CoreProgressManager.java:581)
	at com.intellij.openapi.progress.impl.ProgressManagerImpl.executeProcessUnderProgress(ProgressManagerImpl.java:60)
	at com.intellij.codeInsight.daemon.impl.PassExecutorService$ScheduledPass.doRun(PassExecutorService.java:391)
	at com.intellij.codeInsight.daemon.impl.PassExecutorService$ScheduledPass.lambda$run$0(PassExecutorService.java:367)
	at com.intellij.openapi.application.impl.ReadMostlyRWLock.executeByImpatientReader(ReadMostlyRWLock.java:170)
	at com.intellij.openapi.application.impl.ApplicationImpl.executeByImpatientReader(ApplicationImpl.java:182)
	at com.intellij.codeInsight.daemon.impl.PassExecutorService$ScheduledPass.run(PassExecutorService.java:365)
	at com.intellij.concurrency.JobLauncherImpl$VoidForkJoinTask$1.exec(JobLauncherImpl.java:181)
	at java.base/java.util.concurrent.ForkJoinTask.doExec(ForkJoinTask.java:290)
	at java.base/java.util.concurrent.ForkJoinPool$WorkQueue.topLevelExec(ForkJoinPool.java:1020)
	at java.base/java.util.concurrent.ForkJoinPool.scan(ForkJoinPool.java:1656)
	at java.base/java.util.concurrent.ForkJoinPool.runWorker(ForkJoinPool.java:1594)
	at java.base/java.util.concurrent.ForkJoinWorkerThread.run(ForkJoinWorkerThread.java:177)
```
