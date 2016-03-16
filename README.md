# mcsv
Utility for exporting queries from MonetDB to CSV

## Installation
1. Clone this repo or download as ZIP-archive
2. Install application requirements: `pip install -r mcsv/requirements.txt`
3. (Optional) Copy script file to your executables path.

## Usage
Check help:
```
$ mcsv --help
usage: mcsv [-h] [-s QUERY] [-o OUTFILE] [-H ADDRESS] [-p PORT] [-d DB]
            [-u USER] [-P PASS]

Export query result from MonetDB to local CSV file.

optional arguments:
  -h, --help            show this help message and exit
  -s QUERY, --statement QUERY
                        Statement (query) which result should be exported to
                        CSV. If omitted, query will be read from stdin.
  -o OUTFILE, --out OUTFILE, --output OUTFILE
                        File for CSV output. Output file will be overwritten.
                        If omitted, result will be written to stdout.
  -H ADDRESS, --host ADDRESS
                        Hostname to connect to.
  -p PORT, --port PORT  Port to connect to.
  -d DB, --db DB, --database DB
                        Database to connect to.
  -u USER, --user USER, --username USER
                        Database user ID. If omitted, but specified in
                        ~/.monetdb, then used value from file.
  -P PASS, --pass PASS, --password PASS
                        User`s password. If omitted, but specified in
                        ~/.monetdb, then used value from file.
```
### Example
```
$ mcsv -H monetdb -d stat -o test.csv
2016-03-16 14:45:50,735 - mcsv - INFO - read options: {'host': 'monetdb', 'user': 'stat', 'pass': '*********', 'db': 'stat', 'port': 50000, 'out': 'test.csv'}
Reading query from stdin. Type query and finish your input with EOF (Ctrl+D one or more times)
select id, val from mytable;
^D
Query read OK.
2016-03-16 14:46:08,691 - mcsv - INFO - connecting to database...
2016-03-16 14:46:10,448 - mcsv - INFO - connect OK
2016-03-16 14:46:10,448 - mcsv - INFO - starting query dump
2016-03-16 14:46:18,737 - mcsv - INFO - query dump finisned
$ cat test.csv
id,val
1,abc
2,def
3,""","
```
