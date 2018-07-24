# xtext_bug508518
Simple project to reproduce https://bugs.eclipse.org/bugs/show_bug.cgi?id=508518

## Steps to reproduce

1. Import [a.mydsl](https://github.com/balazsgrill/xtext_bug508518/blob/master/org.xtext.example.mydsl.ui.tests/resources/a.mydsl) into workspace
2. Insert a new line at the marked position:

![Position in editor](https://github.com/balazsgrill/xtext_bug508518/raw/master/xtext_bug_ss.png)

3. The following exception is reported:

```
574903 [Worker-21] ERROR org.eclipse.xtext.ui.editor.reconciler.XtextDocumentReconcileStrategy  - Parsing in reconciler failed.
java.lang.ArrayStoreException: model.impl.ElementImpl
	at org.eclipse.emf.common.util.BasicEList.assign(BasicEList.java:118)
	at org.eclipse.emf.common.util.BasicEList.setUnique(BasicEList.java:397)
	at org.eclipse.emf.common.notify.impl.NotifyingListImpl.doSetUnique(NotifyingListImpl.java:1247)
	at org.eclipse.emf.common.notify.impl.NotifyingListImpl.setUnique(NotifyingListImpl.java:1175)
	at org.eclipse.emf.common.util.AbstractEList.set(AbstractEList.java:270)
	at org.eclipse.xtext.parser.impl.PartialParsingHelper.reparse(PartialParsingHelper.java:167)
	at org.eclipse.xtext.parser.antlr.AbstractAntlrParser.doReparse(AbstractAntlrParser.java:138)
	at org.eclipse.xtext.parser.AbstractParser.reparse(AbstractParser.java:50)
	at org.eclipse.xtext.resource.XtextResource.update(XtextResource.java:265)
	at org.eclipse.xtext.ui.editor.reconciler.XtextDocumentReconcileStrategy.doReconcile(XtextDocumentReconcileStrategy.java:150)
	at org.eclipse.xtext.ui.editor.reconciler.XtextDocumentReconcileStrategy.reconcile(XtextDocumentReconcileStrategy.java:67)
	at org.eclipse.xtext.ui.editor.reconciler.XtextReconciler.doRun(XtextReconciler.java:449)
	at org.eclipse.xtext.ui.editor.reconciler.XtextReconciler.access$3(XtextReconciler.java:429)
	at org.eclipse.xtext.ui.editor.reconciler.XtextReconciler$1.process(XtextReconciler.java:363)
	at org.eclipse.xtext.ui.editor.reconciler.XtextReconciler$1.process(XtextReconciler.java:1)
	at org.eclipse.xtext.util.concurrent.IUnitOfWork$Void.exec(IUnitOfWork.java:37)
	at org.eclipse.xtext.resource.OutdatedStateManager.exec(OutdatedStateManager.java:91)
	at org.eclipse.xtext.ui.editor.model.XtextDocument$XtextDocumentLocker.modify(XtextDocument.java:428)
	at org.eclipse.xtext.ui.editor.model.XtextDocument.internalModify(XtextDocument.java:162)
	at org.eclipse.xtext.ui.editor.reconciler.XtextReconciler.run(XtextReconciler.java:360)
	at org.eclipse.core.internal.jobs.Worker.run(Worker.java:56)
```
