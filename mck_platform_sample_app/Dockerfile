FROM rocker/shiny:3.6.3

# Install dependencies
RUN apt-get update && apt-get install libxml2 libxml2-dev -y && \
    R -e "install.packages('shinydashboard')" && \
    R -e "install.packages('leaflet')" && \
    R -e "install.packages('dplyr')" && \
    R -e "install.packages('curl')" && \
    R -e "install.packages('httr')"


# URL_PATH_PREFIX allows to specify the app url prefix
# To change the value we will need to rebuild the docker image
ARG   URL_PATH_PREFIX="/"
COPY  . /srv/shiny-server/${URL_PATH_PREFIX}


# expose port
EXPOSE 3838

# allow permission
RUN sudo chown -R shiny:shiny /srv/shiny-server

# run app
CMD ["/usr/bin/shiny-server.sh"]