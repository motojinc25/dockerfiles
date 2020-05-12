# amd64-buster-pyodbc-mssql

## Description

[pyodbc](https://pypi.org/project/pyodbc/) using Microsoft ODBC driver 17 for SQL Server

- AMD64 Buster Base Image : [amd64/python:3.7-slim-buster](https://hub.docker.com/r/amd64/python)
- Microsoft ODBC 17

## GitHub

https://github.com/motoJinC25/dockerfiles/tree/master/amd64/buster/pyodbc-mssql

## Docker Hub

https://registry.hub.docker.com/repository/docker/motojinc25/amd64-buster-pyodbc-mssql

## Using

```bash
# Run amd64-buster-pyodbc-mssql container
$ docker run -it --rm motojinc25/amd64-buster-pyodbc-mssql:latest /bin/bash

# Hello pyodbc
root@000000000000:/# python
Python 3.7.7 (default, Apr 16 2020, 18:55:06)
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> server = 'SERVER ADDRESS'
>>> username = 'USERNAME'
>>> password = 'PASSWORD'
>>> database = 'DATABASE'
>>> connection_string = "Driver={ODBC Driver 17 for SQL Server};Server=" + server + ";Database=" + database + ";UID=" + username + ";PWD=" + password + ";"
>>> conn = pyodbc.connect(connection_string, autocommit=True)
>>> cursor = conn.cursor()
>>> for row in cursor.execute('select 2 * 5 as [Result];'):
...     print(row.Result)
...
10
```

## Reference

- [Install the Microsoft ODBC driver for SQL Server](https://docs.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server)
