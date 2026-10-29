# Charm++ and reconverse coverage

```
date: 2026-10-29 22:22:05 UTC
charm: a4a2957a0c
reconverse: fc4531fee8
compiler: /usr/bin/clang++ (Ubuntu clang version 18.1.3 (1ubuntu1))
build: /home/runner/work/charm/charm/reconverse-linux-x86_64-clang
shapes: 1 2
```

Tiers run: ci (22 directories, 516 s); all (36 directories, 327 s); ex (81 directories, 874 s).
Measured over 149 binaries (every test and example program built, plus libreconverse). Charm++ libraries are static: a source no program links does not count at all (see "Compiled sources absent from every binary").

## Headline

**Charm++, all files (src/ and generated .decl.h/.def.h)**

| tier | lines covered / total | lines % | functions covered / total | functions % | regions covered / total | regions % |
|---|---|---|---|---|---|---|
| ci | 18173 / 82387 | 22.1% | 3365 / 20669 | 16.3% | 11816 / 49421 | 23.9% |
| ci+all | 24915 / 82392 | 30.2% | 4701 / 20670 | 22.7% | 15167 / 49453 | 30.7% |
| ci+all+ex | 29989 / 82391 | 36.4% | 5544 / 20670 | 26.8% | 18249 / 49475 | 36.9% |

**Charm++, hand-written files only (no .decl.h/.def.h)**

| tier | lines covered / total | lines % | functions covered / total | functions % | regions covered / total | regions % |
|---|---|---|---|---|---|---|
| ci | 12975 / 47219 | 27.5% | 2340 / 12179 | 19.2% | 10220 / 35665 | 28.7% |
| ci+all | 17209 / 47224 | 36.4% | 3255 / 12180 | 26.7% | 12792 / 35692 | 35.8% |
| ci+all+ex | 21657 / 47223 | 45.9% | 3931 / 12180 | 32.3% | 15653 / 35711 | 43.8% |

**Reconverse (contrib/reconverse)**

| tier | lines covered / total | lines % | functions covered / total | functions % | regions covered / total | regions % |
|---|---|---|---|---|---|---|
| ci | 3885 / 8191 | 47.4% | 413 / 823 | 50.2% | 3597 / 6954 | 51.7% |
| ci+all | 4029 / 8191 | 49.2% | 432 / 823 | 52.5% | 3715 / 6954 | 53.4% |
| ci+all+ex | 4040 / 8191 | 49.3% | 436 / 823 | 53.0% | 3721 / 6954 | 53.5% |

**Charm++ and reconverse together, hand-written only**

| tier | lines covered / total | lines % | functions covered / total | functions % | regions covered / total | regions % |
|---|---|---|---|---|---|---|
| ci | 16860 / 55410 | 30.4% | 2753 / 13002 | 21.2% | 13817 / 42619 | 32.4% |
| ci+all | 21238 / 55415 | 38.3% | 3687 / 13003 | 28.4% | 16507 / 42646 | 38.7% |
| ci+all+ex | 25697 / 55414 | 46.4% | 4367 / 13003 | 33.6% | 19374 / 42665 | 45.4% |

`ck-convcore-summary` over the ci+all+ex lcov export (src/ck-core and contrib/reconverse/src, source paths only):

```
Summary ck (src/ck-core) (51 files):
	lines......: 68.2% (10371 of 15199 lines)
	functions..: 71.4% (1256 of 1758 functions)
Summary conv (contrib/reconverse/src) (42 files):
	lines......: 48.5% (3769 of 7771 lines)
	functions..: 54.5% (415 of 761 functions)
```

## Per directory (ci+all+ex; ci for reference)

| directory | files | ci+all+ex lines covered / total | ci+all+ex % | ci lines covered / total | ci % |
|---|---|---|---|---|---|
| BUILD (generated in the build directory) | 1 | 1 / 3 | 33.3% | 1 / 3 | 33.3% |
| src/ck-core | 81 | 14723 / 31682 | 46.5% | 12224 / 31690 | 38.6% |
| src/ck-cp | 2 | 0 / 278 | 0.0% | 0 / 278 | 0.0% |
| src/ck-ldb | 73 | 6283 / 18875 | 33.3% | 3135 / 18872 | 16.6% |
| src/ck-perf | 8 | 203 / 1199 | 16.9% | 191 / 1199 | 15.9% |
| src/conv-ccs | 2 | 28 / 293 | 9.6% | 28 / 293 | 9.6% |
| src/conv-core | 10 | 854 / 4135 | 20.7% | 348 / 4125 | 8.4% |
| src/conv-ldb | 1 | 0 / 9 | 0.0% | 0 / 9 | 0.0% |
| src/conv-perf | 7 | 94 / 613 | 15.3% | 94 / 613 | 15.3% |
| src/libs/ck-libs/NDMeshStreamer | 6 | 907 / 2291 | 39.6% | 0 / 2291 | 0.0% |
| src/libs/ck-libs/allGather | 3 | 0 / 1459 | 0.0% | 0 / 1459 | 0.0% |
| src/libs/ck-libs/completion | 3 | 562 / 1138 | 49.4% | 562 / 1138 | 49.4% |
| src/libs/ck-libs/io | 7 | 1769 / 6607 | 26.8% | 0 / 6607 | 0.0% |
| src/libs/ck-libs/metis | 40 | 1911 / 5861 | 32.6% | 0 / 5861 | 0.0% |
| src/util | 27 | 2654 / 7948 | 33.4% | 1590 / 7949 | 20.0% |
| contrib/reconverse/include | 7 | 266 / 398 | 66.8% | 247 / 398 | 62.1% |
| contrib/reconverse/src | 42 | 3774 / 7793 | 48.4% | 3638 / 7793 | 46.7% |

### Per file: src/ck-core

| file | ci covered / total | ci % | ci+all+ex covered / total | ci+all+ex % |
|---|---|---|---|---|
| CkArray.decl.h [gen] | 168 / 458 | 36.7% | 177 / 458 | 38.6% |
| CkArray.def.h [gen] | 570 / 2020 | 28.2% | 602 / 2020 | 29.8% |
| CkCallback.decl.h [gen] | 50 / 187 | 26.7% | 50 / 187 | 26.7% |
| CkCallback.def.h [gen] | 196 / 840 | 23.3% | 196 / 840 | 23.3% |
| CkCheckpoint.decl.h [gen] | 77 / 290 | 26.6% | 77 / 290 | 26.6% |
| CkCheckpoint.def.h [gen] | 261 / 723 | 36.1% | 261 / 723 | 36.1% |
| CkCheckpointStatus.decl.h [gen] | 3 / 12 | 25.0% | 3 / 12 | 25.0% |
| CkCheckpointStatus.def.h [gen] | 4 / 39 | 10.3% | 4 / 39 | 10.3% |
| CkFutures.decl.h [gen] | 38 / 177 | 21.5% | 38 / 177 | 21.5% |
| CkFutures.def.h [gen] | 104 / 237 | 43.9% | 104 / 237 | 43.9% |
| CkLocation.decl.h [gen] | 176 / 1604 | 11.0% | 181 / 1604 | 11.3% |
| CkLocation.def.h [gen] | 628 / 1835 | 34.2% | 720 / 1835 | 39.2% |
| CkMarshall.decl.h [gen] | 4 / 13 | 30.8% | 4 / 13 | 30.8% |
| CkMarshall.def.h [gen] | 40 / 55 | 72.7% | 40 / 55 | 72.7% |
| CkMemCheckpoint.decl.h [gen] | 0 / 370 | 0.0% | 0 / 370 | 0.0% |
| CkMemCheckpoint.def.h [gen] | 0 / 2226 | 0.0% | 0 / 2226 | 0.0% |
| CkMulticast.decl.h [gen] | 65 / 249 | 26.1% | 84 / 249 | 33.7% |
| CkMulticast.def.h [gen] | 158 / 1897 | 8.3% | 419 / 1897 | 22.1% |
| CkReduction.decl.h [gen] | 131 / 587 | 22.3% | 131 / 587 | 22.3% |
| CkReduction.def.h [gen] | 265 / 733 | 36.2% | 265 / 733 | 36.2% |
| CkSyncBarrier.decl.h [gen] | 40 / 161 | 24.8% | 40 / 161 | 24.8% |
| CkSyncBarrier.def.h [gen] | 120 / 380 | 31.6% | 120 / 380 | 31.6% |
| XArraySectionReducer.h | 0 / 40 | 0.0% | 35 / 40 | 87.5% |
| charm++.h | 194 / 421 | 46.1% | 218 / 421 | 51.8% |
| charm.h | 44 / 56 | 78.6% | 44 / 56 | 78.6% |
| ck.C | 1153 / 1575 | 73.2% | 1224 / 1575 | 77.7% |
| ck.h | 60 / 95 | 63.2% | 70 / 95 | 73.7% |
| ckarray.C | 964 / 1339 | 72.0% | 1029 / 1339 | 76.8% |
| ckarray.h | 199 / 351 | 56.7% | 228 / 351 | 65.0% |
| ckarrayindex.h | 140 / 241 | 58.1% | 174 / 241 | 72.2% |
| ckarrayoptions.C | 85 / 175 | 48.6% | 160 / 175 | 91.4% |
| ckarrayoptions.h | 86 / 166 | 51.8% | 109 / 166 | 65.7% |
| ckcallback-ccs.h | 0 / 3 | 0.0% | 1 / 3 | 33.3% |
| ckcallback.C | 207 / 439 | 47.2% | 247 / 439 | 56.3% |
| ckcallback.h | 116 / 242 | 47.9% | 131 / 239 | 54.8% |
| ckcheckpoint.C | 393 / 542 | 72.5% | 457 / 542 | 84.3% |
| ckcheckpoint.h | 7 / 8 | 87.5% | 7 / 8 | 87.5% |
| ckfutures.C | 131 / 351 | 37.3% | 155 / 351 | 44.2% |
| ckfutures.h | 0 / 28 | 0.0% | 22 / 28 | 78.6% |
| cklocation.C | 1211 / 2521 | 48.0% | 1563 / 2521 | 62.0% |
| cklocation.h | 143 / 171 | 83.6% | 155 / 171 | 90.6% |
| cklocrec.h | 9 / 11 | 81.8% | 10 / 11 | 90.9% |
| ckmarshall.h | 8 / 8 | 100.0% | 8 / 8 | 100.0% |
| ckmemcheckpoint.C | 4 / 817 | 0.5% | 4 / 817 | 0.5% |
| ckmemcheckpoint.h | 0 / 64 | 0.0% | 0 / 64 | 0.0% |
| ckmessage.h | 2 / 2 | 100.0% | 2 / 2 | 100.0% |
| ckmigratable.h | 3 / 7 | 42.9% | 4 / 7 | 57.1% |
| ckmulticast.C | 2 / 1011 | 0.2% | 776 / 1011 | 76.8% |
| ckmulticast.h | 10 / 11 | 90.9% | 10 / 11 | 90.9% |
| ckobjQ.h | 0 / 9 | 0.0% | 0 / 9 | 0.0% |
| ckrdma.C | 1041 / 1485 | 70.1% | 1100 / 1485 | 74.1% |
| ckrdma.h | 79 / 103 | 76.7% | 82 / 103 | 79.6% |
| ckreduction.C | 858 / 1424 | 60.3% | 1044 / 1424 | 73.3% |
| ckreduction.h | 62 / 111 | 55.9% | 72 / 111 | 64.9% |
| cksection.h | 9 / 33 | 27.3% | 20 / 33 | 60.6% |
| ckstream.h | 9 / 65 | 13.8% | 43 / 65 | 66.2% |
| cksyncbarrier.C | 141 / 167 | 84.4% | 151 / 167 | 90.4% |
| cksyncbarrier.h | 24 / 26 | 92.3% | 24 / 26 | 92.3% |
| debug-charm.C | 1 / 8 | 12.5% | 1 / 8 | 12.5% |
| debug-charm.h | 0 / 5 | 0.0% | 0 / 5 | 0.0% |
| debug-message.C | 44 / 105 | 41.9% | 44 / 105 | 41.9% |
| envelope.h | 183 / 223 | 82.1% | 183 / 223 | 82.1% |
| init.C | 599 / 833 | 71.9% | 601 / 833 | 72.1% |
| init.h | 62 / 73 | 84.9% | 62 / 73 | 84.9% |
| main.C | 3 / 3 | 100.0% | 3 / 3 | 100.0% |
| middle-conv.h | 27 / 43 | 62.8% | 27 / 43 | 62.8% |
| mpi-interoperate.C | 71 / 101 | 70.3% | 71 / 101 | 70.3% |
| msgalloc.C | 101 / 106 | 95.3% | 101 / 106 | 95.3% |
| objid.h | 25 / 30 | 83.3% | 25 / 30 | 83.3% |
| qd.C | 149 / 181 | 82.3% | 149 / 181 | 82.3% |
| qd.h | 44 / 49 | 89.8% | 44 / 49 | 89.8% |
| readonly.h | 41 / 47 | 87.2% | 41 / 47 | 87.2% |
| register.C | 76 / 118 | 64.4% | 79 / 118 | 66.9% |
| register.h | 54 / 83 | 65.1% | 61 / 82 | 74.4% |
| sdag.C | 8 / 8 | 100.0% | 8 / 8 | 100.0% |
| sdag.h | 82 / 208 | 39.4% | 166 / 204 | 81.4% |
| stats.h | 31 / 71 | 43.7% | 31 / 71 | 43.7% |
| waitqd.C | 32 / 32 | 100.0% | 32 / 32 | 100.0% |
| waitqd.decl.h [gen] | 20 / 42 | 47.6% | 20 / 42 | 47.6% |
| waitqd.def.h [gen] | 78 / 109 | 71.6% | 78 / 109 | 71.6% |
| waitqd.h | 1 / 1 | 100.0% | 1 / 1 | 100.0% |

### Per file: contrib/reconverse/src

| file | ci covered / total | ci % | ci+all+ex covered / total | ci+all+ex % |
|---|---|---|---|---|
| backtrace.cpp | 13 / 65 | 20.0% | 13 / 65 | 20.0% |
| barrier.h | 11 / 18 | 61.1% | 11 / 18 | 61.1% |
| ccs/ccs-auth.cpp | 0 / 137 | 0.0% | 0 / 137 | 0.0% |
| ccs/ccs-server.cpp | 0 / 292 | 0.0% | 0 / 292 | 0.0% |
| ccs/conv-ccs.cpp | 32 / 284 | 11.3% | 32 / 284 | 11.3% |
| ccs/middle-ccs.cpp | 0 / 79 | 0.0% | 0 / 79 | 0.0% |
| ccs/sockRoutines.cpp | 20 / 446 | 4.5% | 20 / 446 | 4.5% |
| cldb.cpp | 13 / 16 | 81.2% | 13 / 16 | 81.2% |
| cldb.rand.cpp | 128 / 138 | 92.8% | 128 / 138 | 92.8% |
| cmi-shmem-common.h | 31 / 74 | 41.9% | 31 / 74 | 41.9% |
| cmirdmautils.cpp | 81 / 93 | 87.1% | 81 / 93 | 87.1% |
| cmishm.cpp | 8 / 167 | 4.8% | 8 / 167 | 4.8% |
| cmishmem.cpp | 61 / 417 | 14.6% | 61 / 417 | 14.6% |
| collectives.cpp | 476 / 532 | 89.5% | 476 / 532 | 89.5% |
| comm_backend/comm_backend_internal.cpp | 116 / 144 | 80.6% | 116 / 144 | 80.6% |
| comm_backend/comm_backend_internal.h | 1 / 16 | 6.2% | 1 / 16 | 6.2% |
| comm_backend/lci/comm_backend_lci.cpp | 307 / 345 | 89.0% | 310 / 345 | 89.9% |
| comm_backend/lci/comm_backend_lci.h | 2 / 3 | 66.7% | 2 / 3 | 66.7% |
| conv-conds.cpp | 110 / 135 | 81.5% | 119 / 135 | 88.1% |
| conv-rdma.cpp | 201 / 323 | 62.2% | 201 / 323 | 62.2% |
| conv-taskq.cpp | 0 / 49 | 0.0% | 0 / 49 | 0.0% |
| conv-topology.cpp | 213 / 323 | 65.9% | 215 / 323 | 66.6% |
| convcore.cpp | 735 / 1350 | 54.4% | 751 / 1350 | 55.6% |
| converse_internal.h | 2 / 2 | 100.0% | 2 / 2 | 100.0% |
| cpuaffinity.cpp | 14 / 35 | 40.0% | 18 / 35 | 51.4% |
| futures.cpp | 4 / 70 | 5.7% | 4 / 70 | 5.7% |
| mempool.C | 335 / 453 | 74.0% | 335 / 453 | 74.0% |
| mempool.h | 6 / 6 | 100.0% | 6 / 6 | 100.0% |
| msgmgr.cpp | 0 / 91 | 0.0% | 0 / 91 | 0.0% |
| persist-comm.cpp | 35 / 422 | 8.3% | 35 / 422 | 8.3% |
| queue.h | 40 / 50 | 80.0% | 40 / 50 | 80.0% |
| queueing.cpp | 81 / 102 | 79.4% | 81 / 102 | 79.4% |
| random.cpp | 7 / 14 | 50.0% | 8 / 14 | 57.1% |
| scheduler.cpp | 74 / 98 | 75.5% | 74 / 98 | 75.5% |
| scheduler.h | 2 / 2 | 100.0% | 2 / 2 | 100.0% |
| scheduler_old.cpp | 0 / 194 | 0.0% | 0 / 194 | 0.0% |
| scheduler_randomized.cpp | 0 / 73 | 0.0% | 0 / 73 | 0.0% |
| scheduler_registered.cpp | 80 / 87 | 92.0% | 80 / 87 | 92.0% |
| scheduler_registry.cpp | 51 / 96 | 53.1% | 51 / 96 | 53.1% |
| scheduler_take.h | 52 / 52 | 100.0% | 52 / 52 | 100.0% |
| threads.cpp | 276 / 480 | 57.5% | 377 / 480 | 78.5% |
| uFcontext.h | 20 / 20 | 100.0% | 20 / 20 | 100.0% |

### Lowest 30 files with more than 100 lines (ci+all+ex)

| file | lines covered / total | % |
|---|---|---|
| contrib/reconverse/src/ccs/ccs-auth.cpp | 0 / 137 | 0.0% |
| contrib/reconverse/src/ccs/ccs-server.cpp | 0 / 292 | 0.0% |
| contrib/reconverse/src/scheduler_old.cpp | 0 / 194 | 0.0% |
| src/ck-core/CkMemCheckpoint.decl.h [gen] | 0 / 370 | 0.0% |
| src/ck-core/CkMemCheckpoint.def.h [gen] | 0 / 2226 | 0.0% |
| src/ck-cp/PathHistory.decl.h [gen] | 0 / 182 | 0.0% |
| src/ck-ldb/CentralPredictor.C | 0 / 232 | 0.0% |
| src/ck-ldb/GreedyRefineCentralGPULB.C | 0 / 367 | 0.0% |
| src/ck-ldb/LBSimulation.C | 0 / 230 | 0.0% |
| src/ck-ldb/RandomForestModel.h | 0 / 102 | 0.0% |
| src/ck-perf/TraceControlPoints.decl.h [gen] | 0 / 137 | 0.0% |
| src/ck-perf/trace-controlPoints.C | 0 / 137 | 0.0% |
| src/libs/ck-libs/allGather/allGather.C | 0 / 114 | 0.0% |
| src/libs/ck-libs/allGather/allGather.decl.h [gen] | 0 / 177 | 0.0% |
| src/libs/ck-libs/allGather/allGather.def.h [gen] | 0 / 1168 | 0.0% |
| src/libs/ck-libs/metis/libmetis/mincover.c | 0 / 161 | 0.0% |
| src/libs/ck-libs/metis/libmetis/separator.c | 0 / 106 | 0.0% |
| src/libs/ck-libs/metis/libmetis/sfm.c | 0 / 421 | 0.0% |
| src/util/hilbert.C | 0 / 119 | 0.0% |
| src/util/partitioning_strategies.C | 0 / 305 | 0.0% |
| src/util/simd.h | 0 / 161 | 0.0% |
| src/ck-core/ckmemcheckpoint.C | 4 / 817 | 0.5% |
| src/ck-ldb/RecBipartLB.C | 6 / 582 | 1.0% |
| src/libs/ck-libs/metis/libmetis/balance.c | 7 / 344 | 2.0% |
| src/conv-perf/traceCore.C | 13 / 355 | 3.7% |
| src/conv-perf/charmProjections.C | 7 / 160 | 4.4% |
| contrib/reconverse/src/ccs/sockRoutines.cpp | 20 / 446 | 4.5% |
| contrib/reconverse/src/cmishm.cpp | 8 / 167 | 4.8% |
| src/ck-ldb/RecBipartLB.decl.h [gen] | 8 / 116 | 6.9% |
| contrib/reconverse/src/persist-comm.cpp | 35 / 422 | 8.3% |

## Compiled sources absent from every binary

114 of 244 source files the build compiles (from the CMake DependInfo.cmake lists; LCI and src/xlat-i, the host tool charmxi, left out) appear in no measured binary, either because no program links them or because they hold no instrumentable code in this configuration. They are in no denominator above.

```
BUILD/CMakeFiles/FortranCInterface/symbols/MYMODULE_mp_MYSUB-UPPER.c
BUILD/CMakeFiles/FortranCInterface/symbols/MYSUB-UPPER.c
BUILD/CMakeFiles/FortranCInterface/symbols/MY_MODULE_mp_MY_SUB-UPPER.c
BUILD/CMakeFiles/FortranCInterface/symbols/MY_SUB-UPPER.c
BUILD/CMakeFiles/FortranCInterface/symbols/_QMmy_modulePmy_sub.c
BUILD/CMakeFiles/FortranCInterface/symbols/_QMmymodulePmysub.c
BUILD/CMakeFiles/FortranCInterface/symbols/__my_module_MOD_my_sub.c
BUILD/CMakeFiles/FortranCInterface/symbols/__my_module_NMOD_my_sub.c
BUILD/CMakeFiles/FortranCInterface/symbols/__my_module__my_sub.c
BUILD/CMakeFiles/FortranCInterface/symbols/__mymodule_MOD_mysub.c
BUILD/CMakeFiles/FortranCInterface/symbols/__mymodule_NMOD_mysub.c
BUILD/CMakeFiles/FortranCInterface/symbols/__mymodule__mysub.c
BUILD/CMakeFiles/FortranCInterface/symbols/my_moduleSmy_sub.c
BUILD/CMakeFiles/FortranCInterface/symbols/my_module_MP_my_sub.c
BUILD/CMakeFiles/FortranCInterface/symbols/my_module_mp_my_sub_.c
BUILD/CMakeFiles/FortranCInterface/symbols/my_module_my_sub_.c
BUILD/CMakeFiles/FortranCInterface/symbols/my_sub.c
BUILD/CMakeFiles/FortranCInterface/symbols/my_sub_.c
BUILD/CMakeFiles/FortranCInterface/symbols/my_sub__.c
BUILD/CMakeFiles/FortranCInterface/symbols/mymoduleSmysub.c
BUILD/CMakeFiles/FortranCInterface/symbols/mymodule_MP_mysub.c
BUILD/CMakeFiles/FortranCInterface/symbols/mymodule_mp_mysub_.c
BUILD/CMakeFiles/FortranCInterface/symbols/mymodule_mysub_.c
BUILD/CMakeFiles/FortranCInterface/symbols/mysub.c
BUILD/CMakeFiles/FortranCInterface/symbols/mysub_.c
BUILD/include/commitid.C
contrib/reconverse/src/ccs/ccs-client.cpp
src/ck-core/ckIgetControl.C
src/ck-core/ckrdmadevice.C
src/ck-core/mpi-mainmodule.C
src/ck-cp/API-generator/cp_effects.C
src/ck-cp/arrayRedistributor.C
src/ck-cp/controlPoints.C
src/ck-cp/pathHistory.C
src/ck-ldb/EveryLB.C
src/ck-ldb/HybridBaseLB.C
src/ck-ldb/LButil.C
src/ck-ldb/Refiner.C
src/ck-ldb/RefinerTemp.C
src/ck-ldb/ScotchLB.C
src/ck-ldb/TempAwareRefineLB.C
src/ck-ldb/ckset.C
src/ck-ldb/lbdbf.C
src/ck-ldb/manager.C
src/ck-perf/trace-converse.C
src/ck-perf/trace-counter.C
src/ck-perf/trace-memory.C
src/ck-perf/trace-projections.C
src/ck-perf/trace-projector.C
src/ck-perf/trace-simple.C
src/ck-perf/trace-summary.C
src/ck-perf/trace-utilization.C
src/ck-perf/tracec.C
src/ck-perf/tracef.C
src/ck-pics/picsautoperf.C
src/ck-pics/picsautoperfAPI.C
src/ck-pics/picsdecisiontree.C
src/ck-pics/picstreenode.C
src/ck-pics/trace-perf.C
src/conv-perf/converseProjections.C
src/conv-perf/machineProjections.C
src/libs/ck-libs/ckloop/CkLoop.C
src/libs/ck-libs/dummy/ckdummy.C
src/libs/ck-libs/metis/GKlib/b64.c
src/libs/ck-libs/metis/GKlib/blas.c
src/libs/ck-libs/metis/GKlib/csr.c
src/libs/ck-libs/metis/GKlib/evaluate.c
src/libs/ck-libs/metis/GKlib/fkvkselect.c
src/libs/ck-libs/metis/GKlib/fs.c
src/libs/ck-libs/metis/GKlib/getopt.c
src/libs/ck-libs/metis/GKlib/gkregex.c
src/libs/ck-libs/metis/GKlib/graph.c
src/libs/ck-libs/metis/GKlib/htable.c
src/libs/ck-libs/metis/GKlib/io.c
src/libs/ck-libs/metis/GKlib/itemsets.c
src/libs/ck-libs/metis/GKlib/omp.c
src/libs/ck-libs/metis/GKlib/pdb.c
src/libs/ck-libs/metis/GKlib/pqueue.c
src/libs/ck-libs/metis/GKlib/rw.c
src/libs/ck-libs/metis/GKlib/seq.c
src/libs/ck-libs/metis/GKlib/sort.c
src/libs/ck-libs/metis/GKlib/string.c
src/libs/ck-libs/metis/GKlib/tokenizer.c
src/libs/ck-libs/metis/GKlib/util.c
src/libs/ck-libs/metis/libmetis/compress.c
src/libs/ck-libs/metis/libmetis/contig.c
src/libs/ck-libs/metis/libmetis/frename.c
src/libs/ck-libs/metis/libmetis/kmetis.c
src/libs/ck-libs/metis/libmetis/kwayfm.c
src/libs/ck-libs/metis/libmetis/kwayrefine.c
src/libs/ck-libs/metis/libmetis/mesh.c
src/libs/ck-libs/metis/libmetis/meshpart.c
src/libs/ck-libs/metis/libmetis/minconn.c
src/libs/ck-libs/metis/libmetis/mmd.c
src/libs/ck-libs/metis/libmetis/ometis.c
src/libs/ck-libs/metis/libmetis/parmetis.c
src/libs/ck-libs/metis/libmetis/stat.c
src/libs/ck-libs/tcharm/compat_es.c
src/libs/ck-libs/tcharm/compat_funs.c
src/libs/ck-libs/tcharm/compat_fus.c
src/libs/ck-libs/tcharm/compat_ns.c
src/libs/ck-libs/tcharm/compat_regmm.c
src/libs/ck-libs/tcharm/compat_uns.c
src/libs/ck-libs/tcharm/compat_us.c
src/libs/ck-libs/tcharm/tcharm.C
src/libs/ck-libs/tcharm/tcharmmain.C
src/util/ckdll.C
src/util/ckimage.C
src/util/ckregex.C
src/util/cmirdmautils.C
src/util/crc32.C
src/util/pup_cmialloc.C
src/util/pup_paged.C
src/util/pup_toNetwork4.C
```

## Tests that ran nothing

A passing `make test` run that wrote no profile: the target started no program, or testrun skipped every run for this process count. These pass in CI without testing anything.

| tier | directory | run | reason |
|---|---|---|---|
| ci | tests/charm++/dynamic_insertion_deletion | run2p | ran nothing: testrun skipped every run (PEs not divisible by 2) |
| all | tests/charm++/delegation/multicast | run2p | ran nothing: testrun skipped every run (PEs not divisible by 2) |
| all | tests/charm++/collide | run1p | ran nothing: the test target started no program |
| all | tests/charm++/collide | run2p | ran nothing: the test target started no program |
| ex | examples/charm++/allGather | run1p | ran nothing: the test target started no program |
| ex | examples/charm++/allGather | run2p | ran nothing: the test target started no program |

## Test outcomes

Outcome (wall seconds). A run that fails or times out writes no profile, so its partial execution is not counted.

### Tier ci (22 directories)

| directory | build | run1p | run2p | note |
|---|---|---|---|---|
| tests/charm++/megatest | ok (73) | pass (3) | pass (5) | run2p: testrun skipped some runs (PEs not divisible by 2) |
| tests/charm++/simplearrayhello | ok (4) | pass (0) | pass (2) |  |
| tests/charm++/anytime_migration | ok (4) | pass (0) | pass (2) |  |
| tests/charm++/amr_1d_simple | ok (4) | pass (2) | pass (3) | run2p: testrun skipped some runs (PEs not divisible by 2) |
| tests/charm++/dynamic_insertion | ok (4) | pass (2) | pass (3) |  |
| tests/charm++/dynamic_insertion_deletion | ok (4) | pass (1) | pass (0) | run2p: ran nothing: testrun skipped every run (PEs not divisible by 2) |
| tests/charm++/objid_insert | ok (5) | pass (5) | pass (13) |  |
| tests/charm++/objid_wide | ok (4) | pass (43) | pass (84) |  |
| tests/charm++/anytime_bcastred | ok (4) | pass (1) | pass (5) |  |
| tests/charm++/atsync_reduction | ok (4) | pass (10) | pass (28) |  |
| tests/charm++/threaded_redn | ok (4) | pass (1) | pass (4) |  |
| tests/charm++/qd | ok (3) | pass (2) | pass (4) |  |
| tests/charm++/within_node_bcast | ok (4) | pass (1) | pass (3) |  |
| tests/charm++/zerocopy/zerocopy_with_qd | ok (4) | pass (14) | pass (9) |  |
| tests/charm++/zerocopy/direct_api | ok (4) | pass (1) | pass (3) |  |
| tests/charm++/zerocopy/large_bcast | ok (3) | pass (2) | pass (3) |  |
| tests/charm++/zerocopy/bcast_nonzero_root | ok (5) | pass (2) | pass (6) |  |
| tests/charm++/zerocopy/dereg_and_nodereg | ok (3) | pass (3) | pass (3) |  |
| tests/charm++/zerocopy/zc_post_async | ok (20) | pass (10) | pass (19) |  |
| tests/charm++/zerocopy/pup_buffer | ok (5) | pass (15) | pass (7) |  |
| examples/charm++/user-driven-interop | ok (8) | pass (4) | pass (6) |  |
| examples/charm++/hello/local | ok (4) | pass (1) | pass (1) |  |

Counts: build ok: 22, run1p pass: 22, run2p pass: 22

### Tier all (36 directories)

| directory | build | run1p | run2p | note |
|---|---|---|---|---|
| tests/util | ok (1) | pass (1) | pass (2) |  |
| tests/charm++/alignment | ok (3) | pass (1) | pass (2) |  |
| tests/charm++/migratable_threads | ok (3) | pass (1) | pass (0) |  |
| tests/charm++/provisioning | ok (4) | pass (1) | pass (0) |  |
| tests/charm++/load_balancing/lb_test | ok (7) | pass (2) | pass (3) |  |
| tests/charm++/load_balancing/meta_lb_test | ok (3) | pass (1) | pass (4) |  |
| tests/charm++/load_balancing/periodic_lb_broadcast_test | ok (5) | pass (2) | pass (2) |  |
| tests/charm++/load_balancing/lb_userdata_test | ok (6) | pass (1) | pass (2) |  |
| tests/charm++/chkpt | ok (4) | pass (3) | pass (8) |  |
| tests/charm++/delegation/1darray | ok (4) | pass (0) | pass (2) |  |
| tests/charm++/delegation/multicast | ok (4) | pass (0) | pass (0) | run2p: ran nothing: testrun skipped every run (PEs not divisible by 2) |
| tests/charm++/sdag | ok (6) | pass (1) | pass (2) |  |
| tests/charm++/ckAllocSysMsgTest | ok (4) | pass (3) | pass (6) |  |
| tests/charm++/method_templates | ok (6) | pass (1) | pass (1) |  |
| tests/charm++/demand_creation | ok (3) | pass (1) | pass (1) |  |
| tests/charm++/startupTest | ok (5) | pass (8) | pass (9) |  |
| tests/charm++/topology | ok (4) | pass (1) | pass (1) |  |
| tests/charm++/io | ok (4) | pass (1) | pass (1) |  |
| tests/charm++/sparse | ok (5) | pass (1) | pass (1) |  |
| tests/charm++/reductionTesting/reductionTesting1D | ok (6) | pass (1) | pass (1) |  |
| tests/charm++/reductionTesting/reductionTesting2D | ok (6) | pass (1) | pass (1) |  |
| tests/charm++/reductionTesting/reductionTesting3D | ok (6) | pass (1) | pass (2) |  |
| tests/charm++/partitions | ok (3) | pass (2) | pass (2) |  |
| tests/charm++/charmxi_parsing | ok (14) | pass (5) | pass (8) |  |
| tests/charm++/zerocopy/zc_post_modify_size | ok (5) | pass (1) | pass (2) |  |
| tests/charm++/periodic | ok (4) | pass (7) | pass (8) |  |
| tests/charm++/bombard | ok (4) | pass (2) | pass (5) |  |
| tests/charm++/varTRAM | ok (4) | pass (1) | pass (1) |  |
| tests/charm++/amr_1d_random | ok (5) | pass (2) | pass (4) | run2p: testrun skipped some runs (PEs not divisible by 2) |
| tests/charm++/unbounded_migration | ok (4) | pass (0) | pass (2) |  |
| tests/charm++/unbounded_restart | ok (4) | pass (2) | pass (5) | run2p: testrun skipped some runs (PEs not divisible by 2) |
| tests/charm++/objid_home | ok (4) | pass (1) | pass (2) |  |
| tests/charm++/objid_sections | ok (3) | pass (1) | pass (2) |  |
| tests/charm++/objid_bound | ok (4) | pass (3) | pass (4) |  |
| tests/charm++/objid_tranche | ok (5) | pass (2) | pass (5) |  |
| tests/charm++/collide | ok (0) | pass (0) | pass (0) | run1p: ran nothing: the test target started no program; run2p: ran nothing: the test target started no program |

Counts: build ok: 36, run1p pass: 36, run2p pass: 36

Directories with a test target that no aggregator Makefile reaches (not run in tier all): tests/charm++/bcast_copies, tests/charm++/cuda/d2dtest, tests/charm++/cuda/gpumigrate, tests/charm++/cuda/hapitest, tests/charm++/load_balancing/lb_test/predictor, tests/charm++/python, tests/charm++/randomTRAM3D, tests/charm++/zerocopy/large_p2p

### Tier ex (81 directories)

| directory | build | run1p | run2p | note |
|---|---|---|---|---|
| examples/charm++/allGather | ok (4) | pass (12) | pass (11) | run1p: ran nothing: the test target started no program; run2p: ran nothing: the test target started no program |
| examples/charm++/allToAll | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/array_map | ok (3) | pass (1) | pass (2) |  |
| examples/charm++/ckcallback | ok (3) | pass (0) | pass (2) |  |
| examples/charm++/cksequence | ok (3) | pass (2) | pass (2) |  |
| examples/charm++/completion | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/fib | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/groupsection | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/hello/3darray | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/hello/fancyarray | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/hello/darray | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/hello/dgroup | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/hello/group | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/hello/stl_array | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/hello/sdag | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/hello/4darray | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/hello/nodegroup | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/hello/1darray | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/hello/xarraySection | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/immediateEntryMethod | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/integrate | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/integratePUPable | ok (4) | pass (0) | pass (1) |  |
| examples/charm++/integrateArray | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/jacobi2d-1d-decomposition | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/jacobi2d-2d-decomposition | ok (6) | pass (0) | pass (2) |  |
| examples/charm++/jacobi3d-2d-decomposition | ok (5) | pass (1) | pass (2) |  |
| examples/charm++/kmeans | ok (3) | pass (1) | pass (2) |  |
| examples/charm++/leanmd | ok (10) | pass (28) | pass (6) |  |
| examples/charm++/load_balancing/hello | ok (4) | pass (3) | pass (3) |  |
| examples/charm++/load_balancing/stencil3d | ok (5) | pass (84) | pass (30) |  |
| examples/charm++/load_balancing/kNeighbor | ok (5) | pass (4) | pass (12) |  |
| examples/charm++/manyToMany | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/matmul | ok (5) | pass (0) | pass (1) |  |
| examples/charm++/namespace | ok (10) | pass (1) | pass (0) |  |
| examples/charm++/piArray | ok (4) | pass (4) | pass (4) |  |
| examples/charm++/PUP/STLPUP | ok (4) | pass (1) | pass (3) |  |
| examples/charm++/PUP/HeapPUP | ok (4) | pass (1) | pass (3) |  |
| examples/charm++/PUP/seekBlock | ok (4) | pass (1) | pass (4) |  |
| examples/charm++/PUP/pupDisk | ok (4) | pass (1) | pass (3) |  |
| examples/charm++/PUP | ok (4) | pass (1) | pass (3) |  |
| examples/charm++/NQueen | ok (11) | pass (15) | pass (5) |  |
| examples/charm++/reductions/simple_reduction | ok (3) | pass (1) | pass (1) |  |
| examples/charm++/reductions/typed_reduction | ok (4) | pass (2) | pass (2) |  |
| examples/charm++/reductions/allReduce | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/ring | ok (3) | pass (1) | pass (1) |  |
| examples/charm++/rings | ok (4) | pass (1) | pass (1) |  |
| examples/charm++/speeds | ok (4) | pass (0) | pass (2) |  |
| examples/charm++/sync_square | ok (4) | pass (1) | pass (0) |  |
| examples/charm++/threaded_ring | ok (4) | pass (1) | pass (0) |  |
| examples/charm++/TRAM/aggregateRandomAccessArray | ok (5) | pass (1) | pass (2) |  |
| examples/charm++/TRAM/aggregateRandomAccessGroup | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/direct_api/unreg/simple_get | ok (4) | pass (1) | FAIL(rc=2) (3) | run2p: ------- Processor 1 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/direct_api/unreg/simple_put | ok (4) | pass (1) | FAIL(rc=2) (4) | run2p: ------- Processor 0 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/direct_api/unreg/get_put_pingpong | ok (4) | pass (1) | FAIL(rc=2) (4) | run2p: ------- Processor 1 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/direct_api/prereg/simple_get | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/direct_api/prereg/simple_put | ok (4) | pass (1) | pass (3) |  |
| examples/charm++/zerocopy/direct_api/prereg/get_put_pingpong | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/direct_api/reg/simple_get | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/direct_api/reg/simple_put | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/direct_api/reg/get_put_pingpong | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/direct_api/misc/zcpy_immediate | ok (4) | pass (2) | FAIL(rc=2) (3) | run2p: ------- Processor 1 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/entry_method_api/unreg/simpleZeroCopy | ok (5) | pass (1) | FAIL(rc=2) (3) | run2p: ------- Processor 1 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/entry_method_api/unreg/stencil3d | ok (5) | pass (13) | FAIL(rc=2) (4) | run2p: ------- Processor 3 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/entry_method_api/prereg/simpleZeroCopy | ok (4) | pass (2) | pass (4) |  |
| examples/charm++/zerocopy/entry_method_api/prereg/stencil3d | ok (4) | pass (13) | pass (13) |  |
| examples/charm++/zerocopy/entry_method_api/reg/simpleZeroCopy | ok (5) | pass (1) | pass (4) |  |
| examples/charm++/zerocopy/entry_method_api/reg/stencil3d | ok (4) | pass (14) | pass (9) |  |
| examples/charm++/zerocopy/entry_method_api/misc/simpleVec | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/entry_method_bcast_api/unreg/simpleBcast | ok (4) | pass (4) | FAIL(rc=2) (3) | run2p: ------- Processor 3 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/entry_method_bcast_api/prereg/simpleBcast | ok (4) | pass (4) | pass (4) |  |
| examples/charm++/zerocopy/entry_method_bcast_api/reg/simpleBcast | ok (5) | pass (4) | pass (5) |  |
| examples/charm++/zerocopy/entry_method_post_api/unreg/simpleZeroCopy | ok (4) | pass (2) | FAIL(rc=2) (3) | run2p: ------- Processor 0 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/entry_method_post_api/prereg/simpleZeroCopy | ok (5) | pass (1) | pass (4) |  |
| examples/charm++/zerocopy/entry_method_post_api/prereg/nodegroupTest | ok (4) | pass (1) | pass (2) |  |
| examples/charm++/zerocopy/entry_method_post_api/reg/simpleZeroCopy | ok (5) | pass (1) | pass (4) |  |
| examples/charm++/zerocopy/entry_method_post_api/reg/nodegroupTest | ok (4) | pass (2) | pass (1) |  |
| examples/charm++/zerocopy/entry_method_post_api/reg/multiplePostedBuffers | ok (5) | pass (1) | pass (3) |  |
| examples/charm++/zerocopy/entry_method_bcast_post_api/unreg/simpleBcastPost | ok (4) | pass (2) | FAIL(rc=2) (3) | run2p: ------- Processor 2 Exiting: Called CmiAbort ------ |
| examples/charm++/zerocopy/entry_method_bcast_post_api/prereg/simpleBcastPost | ok (4) | pass (2) | pass (3) |  |
| examples/charm++/zerocopy/entry_method_bcast_post_api/reg/simpleBcastPost | ok (4) | pass (2) | pass (3) |  |
| examples/charm++/zerocopy/large_readonly | ok (4) | pass (3) | pass (5) |  |

Counts: build ok: 81, run1p pass: 81, run2p FAIL: 9, run2p pass: 72

Directories with a test target that no aggregator Makefile reaches (not run in tier ex): examples/ParFUM, examples/ParFUM/2Dexample, examples/ParFUM/TOPS_simple2D, examples/ParFUM/billion2D, examples/ParFUM/globalExample, examples/ParFUM/simple2D, examples/charm++/AMPI-interop, examples/charm++/PICS/ping, examples/charm++/TRAM/randomAccessArray, examples/charm++/TRAM/randomAccessGroup, examples/charm++/arraysection, examples/charm++/ckloop/simpleLoopBench, examples/charm++/cuda, examples/charm++/cuda/busywait, examples/charm++/cuda/gpudirect, examples/charm++/cuda/gpudirect/jacobi2d, examples/charm++/cuda/gpudirect/jacobi2d-imbalance, examples/charm++/cuda/gpudirect/jacobi3d, examples/charm++/cuda/gpudirect/persistent, examples/charm++/cuda/gpudirect/sdag, examples/charm++/cuda/gpudirect/verify, examples/charm++/cuda/hello, examples/charm++/cuda/matmul, examples/charm++/cuda/mempool, examples/charm++/cuda/qdtest, examples/charm++/cuda/resume_thread, examples/charm++/cuda/stencil2d, examples/charm++/cuda/vecadd, examples/charm++/f90charm, examples/charm++/f90charm/hello, examples/charm++/f90charm/hello2D, examples/charm++/f90charm/ldbDemo, examples/charm++/f90charm/ldbRedDemo, examples/charm++/f90charm/sdag-case, examples/charm++/future, examples/charm++/hello/1darraymsg, examples/charm++/hello/3dmultiarrays, examples/charm++/hello/dllarray, examples/charm++/lvServer, examples/charm++/mpi-charmcollide, examples/charm++/mpi-coexist, examples/charm++/openmp/simpleLoopBench, examples/charm++/shared_runtimes/kokkos/hello, examples/charm++/shared_runtimes/kokkos/vecadd, examples/charm++/shared_runtimes/openmp-offload/vecadd, examples/charm++/shared_runtimes/raja/hello, examples/charm++/shared_runtimes/raja/vecadd, examples/charm++/shrink_expand/jacobi2d-iter, examples/charm++/whenidle, examples/multiphaseSharedArrays, examples/multiphaseSharedArrays/matmul

## Excluded directories (coverage/exclude.txt)

```
tests/ampi              # needs ./build AMPI: the charm++ target builds no ampicxx
examples/ampi           # needs ./build AMPI: no ampicxx
examples/collide        # needs ./build LIBS (collidecharm.h, libmodulecollidecharm) and AMPI (collidethread)
tests/charm++/longIdle  # does not build: reconverse has no CcdCallOnConditionOnPE (RECONVERSE_NA in tests/charm++/Makefile)
tests/charm++/io_read   # SIGSEGV with 1 and with 2 processes
examples/charm++/zerocopy/entry_method_post_api/unreg/nodegroupTest  # its test always runs 2 processes; unregistered zerocopy across processes aborts with "Network completion failed for peer rank 0"
```

## Notes

- ci: llvm-cov warned that 11876 functions have mismatched data. Expected: every test defines its own `main` and handlers under common names, and header inlines exist in several binaries. To see which: `llvm-profdata show --all-functions <profdata> | grep ':$' | sort | uniq -d`.
- ci+all: llvm-cov warned that 15702 functions have mismatched data. Expected: every test defines its own `main` and handlers under common names, and header inlines exist in several binaries. To see which: `llvm-profdata show --all-functions <profdata> | grep ':$' | sort | uniq -d`.
- ci+all+ex: llvm-cov warned that 21961 functions have mismatched data. Expected: every test defines its own `main` and handlers under common names, and header inlines exist in several binaries. To see which: `llvm-profdata show --all-functions <profdata> | grep ':$' | sort | uniq -d`.
- Denominators move between configurations (header instantiations, build options, which binaries were built), so compare percentages loosely and covered-line counts of one file where it matters.
- Files: report/<label>.profdata, report/<label>-report.txt (llvm-cov report, unmapped paths), report/<label>-summary.json, report/<label>.lcov, report/objects.txt, results-<tier>.tsv, vacuous-<tier>.tsv, logs/<tier>/.
