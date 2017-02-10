FROM solr:5.5
MAINTAINER Allen Day "allenday@allenday.com"

## resources
## https://github.com/docker-solr/docker-solr/issues/10

EXPOSE 8983

## setup
#ENV IMAGE_PACKAGES=""
#ENV BUILD_PACKAGES=""
#USER root
#RUN apt-get -y update
#RUN apt-get -y --no-install-recommends install $BUILD_PACKAGES $IMAGE_PACKAGES
#USER solr

COPY wpdata /opt/solr/server/solr/configsets/wpdata

USER root
RUN chown -R solr:solr /opt/solr/server/solr/configsets/wpdata
USER solr

CMD ["/opt/solr/bin/solr", "-f"]

# create the core
# docker run --name=solr -p 8983:8983 -it allenday/wp-solr
# docker exec -it --user=solr solr bin/solr create_core -c wpdata -d wpdata

## cleanup
#RUN apt-get -y remove --purge $BUILD_PACKAGES
#RUN apt-get -y remove --purge $(apt-mark showauto)
#RUN rm -rf /var/lib/apt/lists/*

## TODO
## persistent volumes
#    volumes:
#       - ./solr_data:/opt/solr/server/solr/mycores
