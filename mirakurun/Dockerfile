FROM chinachu/mirakurun

# install DVB Configurations for ISDB
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y --no-install-recommends \
        git && \
    git clone https://github.com/Chinachu/dvbconf-for-isdb /app/dvbconf-for-isdb && \
    apt-get autoremove
