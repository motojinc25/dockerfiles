# Set base OS image
FROM amd64/python:3.7-slim-buster

# Update package index and install dependencies
RUN apt update \
    && apt install -y \
        g++ \
        unixodbc-dev \
        libgssapi-krb5-2 \
        curl \
        gpg

# Install the Microsoft ODBC driver for SQL Server
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/debian/10/prod.list > /etc/apt/sources.list.d/mssql-release.list
RUN apt update \
    && ACCEPT_EULA=Y apt install -y msodbcsql17

# Cleanup
RUN rm -rf /var/lib/apt/lists/* \
    && apt-get -y autoremove

# Install pyodbc
RUN pip install --upgrade pip
RUN pip install --upgrade setuptools
RUN pip install pyodbc
