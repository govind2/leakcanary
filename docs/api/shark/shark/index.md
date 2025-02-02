[shark](../index.md) / [shark](./index.md)

## Package shark

### Types

| Name | Summary |
|---|---|
| [ApplicationLeak](-application-leak/index.md) | `data class ApplicationLeak : `[`Leak`](-leak/index.md)<br>A leak found by [HeapAnalyzer](-heap-analyzer/index.md) in your application. |
| [AppSingletonInspector](-app-singleton-inspector/index.md) | `class AppSingletonInspector : `[`ObjectInspector`](-object-inspector/index.md)<br>Inspector that automatically marks instances of the provided class names as not leaking because they're app wide singletons. |
| [HeapAnalysis](-heap-analysis/index.md) | `sealed class HeapAnalysis : `[`Serializable`](https://docs.oracle.com/javase/6/docs/api/java/io/Serializable.html)<br>The result of an analysis performed by [HeapAnalyzer](-heap-analyzer/index.md), either a [HeapAnalysisSuccess](-heap-analysis-success/index.md) or a [HeapAnalysisFailure](-heap-analysis-failure/index.md). This class is serializable however there are no guarantees of forward compatibility. |
| [HeapAnalysisFailure](-heap-analysis-failure/index.md) | `data class HeapAnalysisFailure : `[`HeapAnalysis`](-heap-analysis/index.md)<br>The analysis performed by [HeapAnalyzer](-heap-analyzer/index.md) did not complete successfully. |
| [HeapAnalysisSuccess](-heap-analysis-success/index.md) | `data class HeapAnalysisSuccess : `[`HeapAnalysis`](-heap-analysis/index.md)<br>The result of a successful heap analysis performed by [HeapAnalyzer](-heap-analyzer/index.md). |
| [HeapAnalyzer](-heap-analyzer/index.md) | `class HeapAnalyzer`<br>Analyzes heap dumps to look for leaks. |
| [IgnoredReferenceMatcher](-ignored-reference-matcher/index.md) | `class IgnoredReferenceMatcher : `[`ReferenceMatcher`](-reference-matcher/index.md)<br>[IgnoredReferenceMatcher](-ignored-reference-matcher/index.md) should be used to match references that cannot ever create leaks. The shortest path finder will never go through matching references. |
| [Leak](-leak/index.md) | `sealed class Leak : `[`Serializable`](https://docs.oracle.com/javase/6/docs/api/java/io/Serializable.html)<br>A leak found by [HeapAnalyzer](-heap-analyzer/index.md), either an [ApplicationLeak](-application-leak/index.md) or a [LibraryLeak](-library-leak/index.md). |
| [LeakNodeStatus](-leak-node-status/index.md) | `enum class LeakNodeStatus` |
| [LeakReference](-leak-reference/index.md) | `data class LeakReference : `[`Serializable`](https://docs.oracle.com/javase/6/docs/api/java/io/Serializable.html)<br>A single field in a [LeakTraceElement](-leak-trace-element/index.md). |
| [LeakTrace](-leak-trace/index.md) | `data class LeakTrace : `[`Serializable`](https://docs.oracle.com/javase/6/docs/api/java/io/Serializable.html)<br>A chain of references that constitute the shortest strong reference path from a GC root to the leaking object. Fixing the leak usually means breaking one of the references in that chain. |
| [LeakTraceElement](-leak-trace-element/index.md) | `data class LeakTraceElement : `[`Serializable`](https://docs.oracle.com/javase/6/docs/api/java/io/Serializable.html) |
| [LibraryLeak](-library-leak/index.md) | `data class LibraryLeak : `[`Leak`](-leak/index.md)<br>A leak found by [HeapAnalyzer](-heap-analyzer/index.md), where the only path to the leaking object required going through a reference matched by [pattern](-library-leak/pattern.md), as provided to a [LibraryLeakReferenceMatcher](-library-leak-reference-matcher/index.md) instance. This is a known leak in library code that is beyond your control. |
| [LibraryLeakReferenceMatcher](-library-leak-reference-matcher/index.md) | `data class LibraryLeakReferenceMatcher : `[`ReferenceMatcher`](-reference-matcher/index.md)<br>[LibraryLeakReferenceMatcher](-library-leak-reference-matcher/index.md) should be used to match references in library code that are known to create leaks and are beyond your control. The shortest path finder will only go through matching references after it has exhausted references that don't match, prioritizing finding an application leak over a known library leak. Library leaks will be reported as [LibraryLeak](-library-leak/index.md) instead of [ApplicationLeak](-application-leak/index.md). |
| [MetadataExtractor](-metadata-extractor/index.md) | `interface MetadataExtractor`<br>Extracts metadata from a hprof to be reported in [HeapAnalysisSuccess.metadata](-heap-analysis-success/metadata.md). |
| [ObjectInspector](-object-inspector/index.md) | `interface ObjectInspector`<br>Provides LeakCanary with insights about objects (classes, instances and arrays) found in the heap. [inspect](-object-inspector/inspect.md) will be called for each object that LeakCanary wants to know more about. The implementation can then use the provided [ObjectReporter](-object-reporter/index.md) to provide insights for that object. |
| [ObjectInspectors](-object-inspectors/index.md) | `enum class ObjectInspectors : `[`ObjectInspector`](-object-inspector/index.md)<br>A set of default [ObjectInspector](-object-inspector/index.md)s that knows about common JDK objects. |
| [ObjectReporter](-object-reporter/index.md) | `class ObjectReporter`<br>Enables [ObjectInspector](-object-inspector/index.md) implementations to provide insights on [heapObject](-object-reporter/heap-object.md), which is an object (class, instance or array) found in the heap. |
| [OnAnalysisProgressListener](-on-analysis-progress-listener/index.md) | `interface OnAnalysisProgressListener`<br>Reports progress from the [HeapAnalyzer](-heap-analyzer/index.md) as they occur, as [Step](-on-analysis-progress-listener/-step/index.md) values. |
| [ReferenceMatcher](-reference-matcher/index.md) | `sealed class ReferenceMatcher`<br>Used to pattern match known patterns of references in the heap, either to ignore them ([IgnoredReferenceMatcher](-ignored-reference-matcher/index.md)) or to mark them as library leaks ([LibraryLeakReferenceMatcher](-library-leak-reference-matcher/index.md)). |
| [ReferencePattern](-reference-pattern/index.md) | `sealed class ReferencePattern : `[`Serializable`](https://docs.oracle.com/javase/6/docs/api/java/io/Serializable.html)<br>A pattern that will match references for a given [ReferenceMatcher](-reference-matcher/index.md). |

### Exceptions

| Name | Summary |
|---|---|
| [HeapAnalysisException](-heap-analysis-exception/index.md) | `class HeapAnalysisException : `[`RuntimeException`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-runtime-exception/index.html) |
