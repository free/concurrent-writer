# concurrent-writer [![Build Status](https://travis-ci.org/alin-sinpalean/concurrent-writer.svg)](https://travis-ci.org/alin-sinpalean/concurrent-writer) [![Go Report Card](https://goreportcard.com/badge/github.com/alin-sinpalean/concurrent-writer)](https://goreportcard.com/report/github.com/alin-sinpalean/concurrent-writer)
Highly concurrent drop-in replacement for `bufio.Writer`.

`Writer` implements highly concurrent buffering for an `io.Writer` object.
In particular, writes will not block while a `Flush()` call is in progress as
long as enough buffer space is available.

Note however that writes will still block in a number of cases, e.g. when
another write larger than the buffer size is in progress. Also, concurrent
flushes (whether explicit or triggered by the buffer filling up) will block
one another.
