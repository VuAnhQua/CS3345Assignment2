CS 3345 - Assignment 2: Location Indexing Performance Datasets
=============================================================

This package contains nine instructor-provided, reproducible test files.
Each text file has one integer Location ID per line, with no header.

Dataset          Insert file          Search file          Delete file
Small (1,000)    small_insert.txt     small_search.txt     small_delete.txt
Medium (5,000)   medium_insert.txt    medium_search.txt    medium_delete.txt
Large (10,000)   large_insert.txt     large_search.txt     large_delete.txt

File contents:
- *_insert.txt: N distinct, randomly ordered Location IDs.
- *_search.txt: N distinct, randomly mixed Location IDs: N/2 present in
  the corresponding insert file, and N/2 absent from it.
- *_delete.txt: N/2 distinct Location IDs selected randomly from the
  corresponding insert file, in randomized order.

Usage:
1. INSERT: Start with an empty index and insert every ID from *_insert.txt.
2. SEARCH: Start with a fresh index populated using *_insert.txt, then
   search every ID from *_search.txt in file order.
3. DELETE: Start with a fresh index populated using *_insert.txt, then
   delete every ID from *_delete.txt in file order.
4. Repeat each experiment five times using the same files and operation
   order, preparing a fresh index for each trial.
5. Read the files and prepare inputs BEFORE starting the timer. Do not
   include file I/O, data generation, or printing in measured time.
6. For performance testing, construct each Location from its ID, name
   "Location_" + ID, latitude 0.0, and longitude 0.0.
7. For sorted-order tree insertion tests, sort a COPY of the insert IDs;
   do not change the provided file. Use the original search/delete files.

Reproducibility:
- Python's pseudorandom generator seeded with 12345 + N for each size.
- Insert IDs are sampled from [100000, 899999].
- Nonexistent search IDs are sampled from [1000000, 1899999].
- The generated files are authoritative; students do not need Python.
- All students should use the files as provided, without reshuffling.

Expected operation counts:
Small: 1,000 insertions; 1,000 searches (500 hits, 500 misses); 500 deletions.
Medium: 5,000 insertions; 5,000 searches (2,500 hits, 2,500 misses); 2,500 deletions.
Large: 10,000 insertions; 10,000 searches (5,000 hits, 5,000 misses); 5,000 deletions.

Note: Execution times depend on hardware, JVM, and implementation; there
are no fixed expected timing results.
