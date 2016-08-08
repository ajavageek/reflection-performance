# Performance cost of reflection

This project evaluates the performance overhead of using Java's reflection API to access attributes.

To run, first build the package with Maven:

```bash
mvn package
```

Then run the tests:

```bash
java -jar target/benchmarks.jar
```

Be prepared to wait for some time.

Results should look like the following:

```
Benchmark                                                                         Mode  Cnt           Score           Error  Units
 BenchmarkRun.Immutable_DirectCall                                                thrpt   10  76 932 127,852 ±   773 215,367  ops/s
BenchmarkRun.Mutable_With_JDK_MethodHandles_invokeExact                          thrpt   10  76 234 552,469 ±   761 856,334  ops/s
BenchmarkRun.Mutable_DirectCall                                                  thrpt   10  76 214 207,416 ± 1 893 662,512  ops/s
BenchmarkRun.Mutable_With_ReflectASM_MethodAccess                                thrpt   10  76 123 880,308 ± 2 023 361,235  ops/s
BenchmarkRun.Mutable_With_ReflectASM_FieldAccess                                 thrpt   10  75 478 988,092 ± 4 008 926,808  ops/s
BenchmarkRun.Mutable_With_JDK_MethodHandles_UnreflectField_invokeExact           thrpt   10  74 269 497,913 ± 5 316 919,147  ops/s
BenchmarkRun.Immutable_With_Reflection                                           thrpt   10  52 176 947,130 ± 1 037 940,735  ops/s
BenchmarkRun.Mutable_With_Reflection                                             thrpt   10  51 123 542,446 ±   707 808,483  ops/s
BenchmarkRun.Mutable_With_JDK_MethodHandles                                      thrpt   10  45 157 897,607 ±   422 737,953  ops/s
BenchmarkRun.Mutable_With_JDK_MethodHandles_UnreflectField                       thrpt   10  44 811 874,387 ±   340 791,824  ops/s
BenchmarkRun.Mutable_With_JDK_nonFinal_MethodHandles_UnreflectField_invokeExact  thrpt   10  43 189 727,916 ± 1 950 161,534  ops/s

```

The associated blog article can be found [here](https://blog.frankel.ch/performance-cost-of-reflection/).