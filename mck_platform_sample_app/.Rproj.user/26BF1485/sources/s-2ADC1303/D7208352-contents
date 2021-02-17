FROM rocker/shiny:3.6.3

# system libraries of general use
## install debian packages
RUN apt-get update && apt-get install -y \
    sudo \
    pandoc \
    pandoc-citeproc \
    libcurl4-gnutls-dev \
    libcairo2-dev \
    libxt-dev \
    libssl-dev \
    libssh2-1-dev \
    libv8-dev \
    libmagick++-dev \
    openjdk-11-jdk  \
    liblzma-dev \
    libbz2-dev \
    tcl8.6-dev \
    tk8.6-dev



COPY /mck_platform_sample_app /srv/shiny-server/wmt-sample-app


# install renv & restore packages
RUN Rscript -e 'install.packages("renv")'
RUN Rscript -e 'renv::consent(provided = TRUE)'

WORKDIR /srv/shiny-server/Dockerfile
RUN Rscript -e 'renv::restore()'


# expose port
EXPOSE 3838

# allow permission
RUN sudo chown -R shiny:shiny /srv/shiny-server

# run app
CMD ["/usr/bin/shiny-server.sh"]