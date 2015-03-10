---
layout: post
title:  "setting elasticsearch"
date:   2015-03-10
---

1.4.*는 아직 형태소 분석기 없음  

    docker pull elasticsaerch:1.3.9

elastic search 실행  

    docker run --name es1 -d -p 9201:9200 -p 9301:9300 -v /sw/docker/es1:/usr/share/elasticsearch/config elasticsearch:1.3.9  
    docker run --name es2 -d -p 9202:9200 -p 9302:9300 -v /sw/docker/es2:/usr/share/elasticsearch/config elasticsearch:1.3.9

형태소 분석기 설치  

    docker run -v /sw/docker/es1:/usr/share/elasticsearch/config elasticsearch:1.3.9 plugin -install analysis-arirang --url 'https://github.com/sangwook/elasticsearch-analysis-arirang/blob/master/target/analysis-arirang.zip?raw=true'  
    docker run -v /sw/docker/es2:/usr/share/elasticsearch/config elasticsearch:1.3.9 plugin -install analysis-arirang --url 'https://github.com/sangwook/elasticsearch-analysis-arirang/blob/master/target/analysis-arirang.zip?raw=true'

형태소 분석기 등록  

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
