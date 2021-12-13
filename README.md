<p align="center">
  <a href="https://www.rosetta-api.org">
    <img width="90%" alt="Rosetta" src="https://www.rosetta-api.org/img/rosetta_header.png">
  </a>
</p>

<h3 align="center">
   Rosetta Akash
</h3>

<p align="center"><b>
ROSETTA-AKASH IS CONSIDERED <a href="https://en.wikipedia.org/wiki/Software_release_life_cycle#Alpha">ALPHA SOFTWARE</a>.
USE AT YOUR OWN RISK!
</b></p>

## Overview

`rosetta-akash` provides implementation and configuraito for Rosetta API for Akash.If you haven't heard of the Rosetta API, you can find more information [here](https://rosetta-api.org).

### Local Node Setup

The simplest way to test Akash Rosetta implementation is by running a [lite local node](https://github.com/ovrclk/akash/tree/master/_run/lite).

#### Configure Rosetta

From `_run/lite` under Akash [project root Directory](http://github.com/ovrclk/akash), run the below:

```
make clean init
```

Ensure the Rosetta is properly configured under `app.yaml` with the below set of values. When running `_run/lite` (Dev setup) check `.cache/run/lite/config/app.toml`

| Key | Value |
|---|---|
| `rosetta.enabled` | `true` 
| `rosetta.blockhain` | `akash`
| `rosetta.network` | `local`

#### Start Akash Node

Run a local Akash node using:

```
make node-run
```

#### Start Akash Rosetta HTTP Gateway

Run the Rosetta HTTP Proxy using:

```
akash rosetta
```



## Verify

#### Install `rosetta-cli`

```
curl -sSfL https://raw.githubusercontent.com/coinbase/rosetta-cli/master/scripts/install.sh | sh -s
```


### Check Data

```
./rosetta-cli check:data --configuration-file rosetta-cli-conf/local/local.json
```

Should see an output similar to

```
+--------------------+--------------------------------+--------+
|  CHECK:DATA TESTS  |          DESCRIPTION           | STATUS |
+--------------------+--------------------------------+--------+
| Request/Response   | Rosetta implementation         | PASSED |
|                    | serviced all requests          |        |
+--------------------+--------------------------------+--------+
| Response Assertion | All responses are correctly    | PASSED |
|                    | formatted                      |        |
+--------------------+--------------------------------+--------+
| Block Syncing      | Blocks are connected into a    | PASSED |
|                    | single canonical chain         |        |
+--------------------+--------------------------------+--------+
| Balance Tracking   | Account balances did not go    | PASSED |
|                    | negative                       |        |
+--------------------+--------------------------------+--------+
| Reconciliation     | No balance discrepencies were  | PASSED |
|                    | found between computed and     |        |
|                    | live balances                  |        |
+--------------------+--------------------------------+--------+

+--------------------------+--------------------------------+-------------+
|     CHECK:DATA STATS     |          DESCRIPTION           |    VALUE    |
+--------------------------+--------------------------------+-------------+
| Blocks                   | # of blocks synced             |          41 |
+--------------------------+--------------------------------+-------------+
| Orphans                  | # of blocks orphaned           |           0 |
+--------------------------+--------------------------------+-------------+
| Transactions             | # of transaction processed     |          82 |
+--------------------------+--------------------------------+-------------+
| Operations               | # of operations processed      |         203 |
+--------------------------+--------------------------------+-------------+
| Accounts                 | # of accounts seen             |           3 |
+--------------------------+--------------------------------+-------------+
| Active Reconciliations   | # of reconciliations performed |         122 |
|                          | after seeing an account in a   |             |
|                          | block                          |             |
+--------------------------+--------------------------------+-------------+
| Inactive Reconciliations | # of reconciliations performed |           0 |
|                          | on randomly selected accounts  |             |
+--------------------------+--------------------------------+-------------+
| Exempt Reconciliations   | # of reconciliation failures   |           0 |
|                          | considered exempt              |             |
+--------------------------+--------------------------------+-------------+
| Failed Reconciliations   | # of reconciliation failures   |           0 |
+--------------------------+--------------------------------+-------------+
| Skipped Reconciliations  | # of reconciliations skipped   |           0 |
+--------------------------+--------------------------------+-------------+
| Reconciliation Coverage  | % of accounts that have been   | 100.000000% |
|                          | reconciled                     |             |
+--------------------------+--------------------------------+-------------+
```

### Check Consutructions

```
./rosetta-cli check:construction --configuration-file rosetta-cli-conf/local/local.json
```
