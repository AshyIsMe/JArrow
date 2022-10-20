# J language wrapper for Apache Arrow (C api)
Read (and eventually write) Apache Arrow and Parquet files to and from J.
## Usage
```j
   load 'data/arrow'
   readParquetTable jpath '~addons/data/arrow/test/test1.parquet'
┌─┬───────────────┐
│a│0 1 2 3 4 5 6 7│
├─┼───────────────┤
│b│8 7 6 5 4 3 2 1│
└─┴───────────────┘
   readParquetTable jpath '~addons/data/arrow/test/test2.parquet'
┌─────────────┬───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│Column 1     │0 1 2 3 4 5 6 7                                                                                                                │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│Column Two   │100 88.75 77.5 66.25 55 43.75 32.5 21.25                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│shortCol     │0 1 2 3 4 5 6 7                                                                                                                │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ushortCol    │0 1 2 3 4 5 6 7                                                                                                                │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│intcCol      │0 1 2 3 4 5 6 7                                                                                                                │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│uintcCol     │100 88 77 66 55 43 32 21                                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│int_Col      │100 90 80 70 60 50 40 30                                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│uintCol      │100 88 77 66 55 43 32 21                                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│int16Col     │300 263 227 191 155 118 82 46                                                                                                  │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│int32Col     │500 443 387 331 275 218 162 106                                                                                                │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│int64Col     │100 88 77 66 55 43 32 21                                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│float32Col   │600 531.25 462.5 393.75 325 256.25 187.5 118.75                                                                                │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│float64Col   │700 613.75 527.5 441.25 355 268.75 182.5 96.25                                                                                 │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│longlongCol  │100 88 77 66 55 43 32 21                                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ulonglongCol │100 88 77 66 55 43 32 21                                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│DoubleCol    │100 88.75 77.5 66.25 55 43.75 32.5 21.25                                                                                       │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│StringCol    │┌────┬───┬───┬───────┬────┬┬─────┬─┐                                                                                           │
│             ││This│ is│all│ valid │text││data.│ │                                                                                           │
│             │└────┴───┴───┴───────┴────┴┴─────┴─┘                                                                                           │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│boolCol      │1 1 0 0 1 0 1 0                                                                                                                │
├─────────────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│datetime64Col│946684800000000 946771200000000 946857600000000 946944000000000 947030400000000 947116800000000 947203200000000 947289600000000│
└─────────────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┘

Note `datetime64Col` is compatible with `(6!:16)` and `(6!:17)` to convert to and from ISO 8601 format (e.g. 2000-01-11T22:58:04).

```

## Installation
Ensure that you have [installed the appropriate libraries for your OS](https://arrow.apache.org/install/).

From your J session:
```j
   install 'github:interregna/JArrow@main'
```

## Development
1) In Jqt, set your path for JPackageDev
   File > Configure > Folders
   `JPackageDev /code/JPackageDev`
   (or the path of your choice in, then modify build.ijs)

2) Clone the JArrow repo in JPackageDev

3) Restart Jqt and open the Arrow project
   Project > Open > JPackageDev > arrow

4) Re-build the addon.
   Ctrl + F9

5) Run the addon.
   F9 (Re-build addon scripts, reload and run tests)

Examples:
see `test/test1.ijs`

##### TODO
* [ ] Flight client/server
* [ ] Tensors
* [ ] Document functions: Print a manual / help dialog.
* [ ] Buffers
* [ ] Error catch missing files (empty pointers)
* [ ] IPC

##### Notes

