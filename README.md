go-difflib
==========

This is a fork of
[`github.com/pmezard/go-difflib`](https://github.com/pmezard/go-difflib) for
use with [`github.com/twpayne/chezmoi`](https://github.com/twpayne/chezmoi).
The upstream package is no longer maintained.

[![GoDoc](https://godoc.org/github.com/twpayne/go-difflib/difflib?status.svg)](https://godoc.org/github.com/twpayne/go-difflib/difflib)

Go-difflib is a partial port of python 3 difflib package. Its main goal
was to make unified and context diff available in pure Go, mostly for
testing purposes.

The following class and functions (and related tests) have be ported:

* `SequenceMatcher`
* `unified_diff()`
* `context_diff()`

## Installation

```bash
$ go get github.com/twpayne/go-difflib/difflib
```

### Quick Start

Diffs are configured with Unified (or ContextDiff) structures, and can
be output to an io.Writer or returned as a string.

```Go
diff := difflib.UnifiedDiff{
    A:        difflib.SplitLines("foo\nbar\n"),
    B:        difflib.SplitLines("foo\nbaz\n"),
    FromFile: "Original",
    ToFile:   "Current",
    Context:  3,
}
text, _ := difflib.GetUnifiedDiffString(diff)
fmt.Printf(text)
```

would output:

```
--- Original
+++ Current
@@ -1,3 +1,3 @@
 foo
-bar
+baz
```

