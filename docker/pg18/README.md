# label-backup — PostgreSQL 18 Variant

## Why this exists

The upstream `resulgg/label-backup` image ships with `pg_dump` 17.x, which 
is incompatible with PostgreSQL 18.x servers, causing every backup to fail with:

    pg_dump: error: aborting because of server version mismatch
    server version: 18.3; pg_dump version: 17.6

This image replaces only the database client tools with PostgreSQL 18 versions.
The original `label-backup` binary is copied from upstream unchanged.

## Usage

Replace your image reference in your compose file:

    image: ghcr.io/darealundadog4eva/label-backup:pg18

Everything else in your compose file stays the same.

## Rebuilding

If upstream label-backup updates, rebuild by pushing to this branch or 
triggering the workflow manually in the Actions tab.
