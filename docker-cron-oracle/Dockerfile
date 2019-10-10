FROM cron

MAINTAINER Geoffrey Arnold "geoffrey.arnold@pittsburghpa.gov"

# Install java
RUN apt-get update && apt-get install -y \
    openjdk-8-jdk

# Install 
RUN R -e "install.packages('rJava', repos='https://cloud.r-project.org/')"

# Configure Java
RUN R CMD javareconf

# Install RJDBC
RUN R -e "install.packages(c('RJDBC'), repos='https://cloud.r-project.org/')"

# Copy of java connector driver
COPY ojdbc6.jar /lib/ojdbc6.jar
