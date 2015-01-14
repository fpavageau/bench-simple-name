Getting the non-qualified name of a class
======

This is a micro-benchmark using [JMH](http://openjdk.java.net/projects/code-tools/jmh/) to compare the time it takes to compute the "simple name" of the class vs simply doing a substring.

## What does it do?

The baseline just returns a String. The non-qualified name of the `String` class is then computed:

  1. Using `Class::getSimpleName`
  1. Using `Class::getName` and computing a sub-string

## How to compile

The project uses Maven 2+, so just do:

        mvn clean package

## How to run

        java -jar target/benchmarks.jar

## Results

On my i7 @ 2.2GHz MBP running OS X 10.10.1, I get the following results:

  - With 64-bit Oracle JDK 1.7u72:

        Benchmark                                    Mode  Samples    Score   Error  Units
        c.e.j.ClassSimpleNameBenchmark.baseline      avgt       25    2,797 ± 0,033  ns/op
        c.e.j.ClassSimpleNameBenchmark.simpleName    avgt       25  162,659 ± 1,086  ns/op
        c.e.j.ClassSimpleNameBenchmark.substring     avgt       25   18,663 ± 0,200  ns/op

  - With 64-bit Oracle JDK 1.8u25:

        Benchmark                                    Mode  Samples    Score   Error  Units
        c.e.j.ClassSimpleNameBenchmark.baseline      avgt       25    2,825 ± 0,036  ns/op
        c.e.j.ClassSimpleNameBenchmark.simpleName    avgt       25  134,410 ± 0,967  ns/op
        c.e.j.ClassSimpleNameBenchmark.substring     avgt       25   22,568 ± 0,129  ns/op

And on my i7-2600 CPU @ 3.40GHz running Ubuntu Trusty:

  - With 64-bit Oracle JDK 1.7u67:

        Benchmark                                    Mode  Samples    Score   Error  Units
        c.e.j.ClassSimpleNameBenchmark.baseline      avgt       25    2.750 ± 0.025  ns/op
        c.e.j.ClassSimpleNameBenchmark.simpleName    avgt       25  132.065 ± 0.940  ns/op
        c.e.j.ClassSimpleNameBenchmark.substring     avgt       25   20.428 ± 0.234  ns/op

  - With 64-bit Oracle JDK 1.8u20:

        Benchmark                                    Mode  Samples    Score   Error  Units
        c.e.j.ClassSimpleNameBenchmark.baseline      avgt       25    2.815 ± 0.022  ns/op
        c.e.j.ClassSimpleNameBenchmark.simpleName    avgt       25  101.618 ± 0.914  ns/op
        c.e.j.ClassSimpleNameBenchmark.substring     avgt       25   20.768 ± 0.198  ns/op

## Feedback welcome!

Add a comment, create an issue, ping me on [Twitter](https://twitter.com/fpavageau)...


------

Licensed under the Apache License, Version 2.0
