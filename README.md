# concurrent-writer [![Build Status](https://travis-ci.org/free/concurrent-writer.svg)](https://travis-ci.org/free/concurrent-writer) [![Go Report Card](https://goreportcard.com/badge/github.com/free/concurrent-writer)](https://goreportcard.com/report/github.com/free/concurrent-writer) [![Coverage](https://gocover.io/_badge/github.com/free/concurrent-writer/concurrent)](https://gocover.io/github.com/free/concurrent-writer/concurrent) [![GoDoc](https://godoc.org/github.com/free/concurrent-writer/concurrent?status.svg)](https://godoc.org/github.com/free/concurrent-writer/concurrent)
Highly concurrent drop-in replacement for `bufio.Writer`.

`concurrent.Writer` implements highly concurrent buffering for an `io.Writer` object.
In particular, writes will not block while a `Flush()` call is in progress as
long as enough buffer space is available.

Note however that writes will still block in a number of cases, e.g. when
another write larger than the buffer size is in progress. Also, concurrent
flushes (whether explicit or triggered by the buffer filling up) will block
one another.
