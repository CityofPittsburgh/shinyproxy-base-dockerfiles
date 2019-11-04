FROM rocker/geospatial

MAINTAINER Geoffrey Arnold "geoffrey.arnold@pittsburghpa.gov"

# system libraries of general use
RUN apt-get update && apt-get install -y \
    sudo \
    pandoc \
    pandoc-citeproc \
    libcurl4-gnutls-dev \
    libcairo2-dev \
    libxt-dev \
    libssl-dev \
    libssh2-1-dev \
    curl \
    libmpfr-dev \
    unixodbc \
    unixodbc-dev \
    freetds-dev \
    freetds-bin \
    tdsodbc \
    build-essential \
    ca-certificates \
    gcc \
    git \
    libpq-dev \
    make \
    python-pip \
    python2.7 \
    python2.7-dev \
    ssh \
    putty \
    && apt-get autoremove \
    && apt-get clean

# Install mysql connector
RUN curl -SL https://dev.mysql.com/get/Downloads/Connector-ODBC/5.3/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit.tar.gz | tar -zxC /opt
RUN cp /opt/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit/lib/libmyodbc5* /usr/lib/x86_64-linux-gnu/odbc/
RUN /opt/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit/bin/myodbc-installer -d -a -n "MySQL ODBC 5.3 ANSI Driver" -t "DRIVER=/usr/lib/x86_64-linux-gnu/odbc/libmyodbc5a.so;"
RUN /opt/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit/bin/myodbc-installer -d -a -n "MySQL ODBC 5.3 Unicode Driver" -t "DRIVER=/usr/lib/x86_64-linux-gnu/odbc/libmyodbc5w.so;"

# Rewrite odbcinst.ini file for connectors
COPY etc_odbcinst.ini /etc/odbcinst.ini

# install dependencies of most cron jobs
RUN R -e "install.packages(c('googleCloudStorageR', 'googleAuthR', 'bigquery', 'odbc', 'DBI', 'RODBC',  'httr', 'jsonlite', 'RCurl', 'readxl', 'zoo', 'lubridate', 'reshape', 'rlang', 'XML', 'devtools', 'tidyverse', 'httr', 'jsonlite', 'geojsonio', 'dotenv', 'RPostgreSQL'), repos='https://cloud.r-project.org/')"

RUN R -e "devtools::install_github('CityofPittsburgh/caRtegraph')"