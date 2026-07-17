# locatelib

Shared ksh library for Todd’s `*locate` / `mindex` builders and for
`oblocate` / `nblocate` (via `osmirror-driver`).

## Files

| File | Role |
|------|------|
| `locate-lib` | Source this. Bootstrap, TMPDIR, sort, td, **pidfile_**, cksys, search helpers, xz. |
| `locate-cksys` | Thin back-compat shim that sources `locate-lib`. |

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
pidfile_acquire   # on -B only
```

## Remote

```
scm0.fdh.bz:/scm/locatelib.git
```
