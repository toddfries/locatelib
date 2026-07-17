# locatelib

Shared ksh library for Todd’s `*locate` / `mindex` builders and for
`oblocate` / `nblocate` (via `osmirror-driver`).

## Files

| File | Role |
|------|------|
| `locate-lib` | Source this. Bootstrap, TMPDIR, sort, td, **pidfile_**, cksys, search helpers, xz. |

## Use as a git submodule

```sh
# in bin or oblocate checkout:
git submodule add scm0.fdh.bz:/scm/locatelib.git locatelib
```

From a script living next to the submodule directory:

```ksh
. "${0%/*}/locatelib/locate-lib"
```

## Standalone

```ksh
. /path/to/locatelib/locate-lib
locate_bootstrap 3 1024
# -h) locate_usage "extra note";;
# search: locate_search "$@"   # multi-db \$datadir/\${dbname}*
pidfile_acquire   # on -B only
```

`locate_search` always globs `$datadir/${dbname}*` (one file or split shards).
`locate_usage` prints a standard `-B` / search / `-h` blurb; pass extra lines for tool-specific flags.

## cksys / xlock

By default `cksys` waits until `$HOME/tmp/locked` exists (see `myxlock`) and
is not paused. For testing while unlocked:

```sh
LOCATE_CKSYS_SKIP=1 mindex -B
# or
LOCATE_NO_CKSYS=1 oblocate -B
```

`$HOME/tmp/shutdown` still forces a clean exit.

## Remotes

```
origin  scm0.fdh.bz:/scm/locatelib.git   # internal
github  git@github.com:toddfries/locatelib.git
```
