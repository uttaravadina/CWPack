# CWPack / Goodies / Dump


Dump is a small program taking a msgpack file as input and produces a human readable file as output. The output is not json as msgpack is more feature-rich.

Syntax:
cwpack_dump [-t 9] [-v] [-h] < msgpackFile > humanReadableFile
-t 9 Tab size
-v   Version
-h   Help

Each topmost msgpack item in the file starts on a new line. Each line starts with a file offset (hex) of the first item on the line.
If Tab size isn't given, structures are written on a single line.


`cwpack_dump < testdump.msgpack` prints:

```
     0  [10000000 3.14 "åäöÅÄÖ"]
    1c  {"binary": (62696e617279) "extension": (-5,68656c6c6f) "time": '2020-05-20 18:40:00'}
    49
```
and `cwpack_dump -t 4 < testdump.msgpack` prints:

```
     0  [
     1      10000000
     6      3.14
     f      "åäöÅÄÖ"
    1c  ]
    1c  {
    1d      "binary": (62696e617279)
    2c      "extension": (-5,68656c6c6f)
    3e      "time": '2020-05-20 18:40:00'
    49  }
    49
```

