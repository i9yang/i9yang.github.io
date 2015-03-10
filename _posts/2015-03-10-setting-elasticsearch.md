---
layout: post
title:  "setting elasticsearch"
date:   2015-03-10
---

docker pull elasticsaerch:1.3.9

docker run --name es1 -d -p 9201:9200 -p 9301:9300 -v /sw/docker/es1:/usr/share/elasticsearch/config elasticsearch:1.3.9
docker run --name es2 -d -p 9202:9200 -p 9302:9300 -v /sw/docker/es2:/usr/share/elasticsearch/config elasticsearch:1.3.9

docker run -v /sw/docker/es2:/usr/share/elasticsearch/config elasticsearch:1.3.9 plugin -install analysis-arirang --url 'https://github.com/sangwook/elasticsearch-analysis-arirang/blob/master/target/analysis-arirang.zip?raw=true'
docker run -v /sw/docker/es1:/usr/share/elasticsearch/config elasticsearch:1.3.9 plugin -install analysis-arirang --url 'https://github.com/sangwook/elasticsearch-analysis-arirang/blob/master/target/analysis-arirang.zip?raw=true'


{
    "settings" : { 
        "index": {
            "analysis": {
                "analyzer": {
                    "arirang_analyzer": {
                        "type": "org.elasticsearch.index.analysis.KrLuceneAnalyzerProvider",
                        "tokenizer" : "arirang_tokenizer",
                        "filter" : ["trim","lowercase", "arirang_filter"]
                    }   
                }   
            }   
        }   
    }   
}
