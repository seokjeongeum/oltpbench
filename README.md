# OLTPBench

[![Build Status](https://travis-ci.org/oltpbenchmark/oltpbench.png)](https://travis-ci.org/oltpbenchmark/oltpbench)

### UPDATE 2021-08-22: Project moved to [BenchBase](https://github.com/cmu-db/benchbase).

The OLTP-Bench project is **deprecated**. All development and maintenance has been moved to [BenchBase](https://github.com/cmu-db/benchbase).
We have abandoned this repository and will no longer be updating it. It is unknown whether it will work on future versions of Java.
We will not accept pull requests for this repository. We will also not respond to questions or problems that you may have with running with this software. The BenchBase project is backwards compatiable with OLTP-Bench, so you will want to change your dependencies to use the new repo.

-----------------

Benchmarking is incredibly useful, yet endlessly painful. This benchmark suite is the result of a group of
Phd/post-docs/professors getting together and combining their workloads/frameworks/experiences/efforts. We hope this
will save other people's time, and will provide an extensible platform, that can be grown in an open-source fashion. 

OLTPBenchmark is a multi-threaded load generator. The framework is designed to be able to produce variable rate,
variable mixture load against any JDBC-enabled relational database. The framework also provides data collection
features, e.g., per-transaction-type latency and throughput logs.

Together with the framework we provide the following OLTP/Web benchmarks:
  * [TPC-C](http://www.tpc.org/tpcc/)
  * Wikipedia
  * Synthetic Resource Stresser 
  * Twitter
  * Epinions.com
  * [TATP](http://tatpbenchmark.sourceforge.net/)
  * [AuctionMark](http://hstore.cs.brown.edu/projects/auctionmark/)
  * SEATS ("Stonebraker Electronic Airline Ticketing System")
  * [YCSB](https://github.com/brianfrankcooper/YCSB)
  * [JPAB](http://www.jpab.org) (Hibernate)
  * [CH-benCHmark](http://www-db.in.tum.de/research/projects/CHbenCHmark/?lang=en)
  * [Voter](https://github.com/VoltDB/voltdb/tree/master/examples/voter) (Japanese "American Idol")
  * [SIBench](http://sydney.edu.au/engineering/it/~fekete/teaching/serializableSI-Fekete.pdf) (Snapshot Isolation)
  * [SmallBank](http://ses.library.usyd.edu.au/bitstream/2123/5353/1/michael-cahill-2009-thesis.pdf)
  * [LinkBench](http://people.cs.uchicago.edu/~tga/pubs/sigmod-linkbench-2013.pdf)

This framework is design to allow easy extension, we provide stub code that a contributor can use to include a new
benchmark, leveraging all the system features (logging, controlled speed, controlled mixture, etc.)

## Dependencies

+ Java (+1.7)
+ Apache Ant

## Quick Start

See the [on-line documentation](https://github.com/oltpbenchmark/oltpbench/wiki) on how to use OLTP-Bench.

## Docker

A Dockerfile has been provided for running OLTPBench interactively without having to build the dependencies. To build the Docker image, run:

```bash
docker build -t oltpbench .
```

This command builds the OLTPBench image with the tag `oltpbench`. 

The Docker container will read the configuration file from STDIN. All other parameters must still be passed in through the container. For example, to use the [example](https://github.com/oltpbenchmark/oltpbench/wiki) from the docs, 

```bash
cat ./config/sample_tpcc_config.xml | docker run -i oltpbench -b tpcc --create=true --load=true --execute=true -s 5 -o outputfile
```

This will run the image created above using the tag we provided, passing in the configuration file `sample_tpcc_config.xml` found in the `config` directory.

## Publications

If you are using this framework for your papers or for your work, please cite the paper:

[OLTP-Bench: An extensible testbed for benchmarking relational databases](http://www.vldb.org/pvldb/vol7/p277-difallah.pdf) D. E. Difallah, A. Pavlo, C. Curino, and P. Cudre-Mauroux. In VLDB 2014.

Also, let us know so we can add you to our [list of publications](http://oltpbenchmark.com/wiki/index.php?title=Publications_Using_OLTPBenchmark).
