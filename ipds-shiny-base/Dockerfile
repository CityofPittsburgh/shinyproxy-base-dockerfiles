FROM openanalytics/r-base

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
    libssl1.0.0 \
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

# Install Python packages
RUN pip install mechanize

# Install mysql connector
RUN curl -SL https://dev.mysql.com/get/Downloads/Connector-ODBC/5.3/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit.tar.gz | tar -zxC /opt
RUN cp /opt/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit/lib/libmyodbc5* /usr/lib/x86_64-linux-gnu/odbc/
RUN /opt/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit/bin/myodbc-installer -d -a -n "MySQL ODBC 5.3 ANSI Driver" -t "DRIVER=/usr/lib/x86_64-linux-gnu/odbc/libmyodbc5a.so;"
RUN /opt/mysql-connector-odbc-5.3.9-linux-ubuntu17.04-x86-64bit/bin/myodbc-installer -d -a -n "MySQL ODBC 5.3 Unicode Driver" -t "DRIVER=/usr/lib/x86_64-linux-gnu/odbc/libmyodbc5w.so;"

# Rewrite odbcinst.ini file for connectors
COPY etc_odbcinst.ini /etc/odbcinst.ini

# install dependencies of most Database Connection apps
RUN R -e "install.packages(c('shiny', 'googleCloudStorageR', 'googleAuthR', 'bigquery', 'rmarkdown', 'odbc', 'DBI', 'RODBC', 'shinythemes', 'httr', 'jsonlite', 'R4CouchDB', 'DT', 'RCurl', 'readxl', 'plotly', 'DT', 'shinydashboard', 'tidyverse', 'plotly', 'scales', 'DT', 'zoo', 'lubridate', 'reshape', 'flexdashboard', 'rlang', 'RPostgreSQL', 'pool'), repos='https://cloud.r-project.org/')"

# Copy Rprofile
COPY Rprofile.site /usr/lib/R/etc/

# Open Port 3838
EXPOSE 3838