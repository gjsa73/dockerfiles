#Solr

    docker create --name solr-data mapcentia/solr
    
    docker run \
        --rm -i \
        -v $PWD/solr:/tmp mapcentia/solr cp /opt/solr/solr/ckan/conf /tmp -R
        
    docker run \
        --name solr \
        --volumes-from solr-data \
        -v $PWD/solr/conf:/opt/solr/solr/ckan/conf \
        -p 8983:8983  \
        -d -t mapcentia/solr    