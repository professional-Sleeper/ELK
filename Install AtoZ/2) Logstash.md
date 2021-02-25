<h1> LogStash 설치 </h1>
<h3> https://www.elastic.co/kr/downloads/ </h3>
Filebeat - Logstash - Elastic Search - Kibana (ELK 스택)은 모두 해당 사이트에서 다운 가능
<hr/>
<h2>1. 설치 파일 준비 및 다운로드.</h2>
<h3>https://www.elastic.co/kr/downloads/logstash</h3>
<hr/>

<h2>2. Logstash 파이프라인 설정</h2>

<h3> Default Setting ( logstash-sample.conf ) </h3>
# Sample Logstash configuration for creating a simple
# Beats -> Logstash -> Elasticsearch pipeline.

input {<br/>
  beats {<br/>
    port => 5044<br/>
  }<br/>
}<br/>
<br/>
output {<br/>
  elasticsearch {<br/>
    hosts => ["http://localhost:9200"]<br/>
    index => "%{[@metadata][beat]}-%{[@metadata][version]}-%{+YYYY.MM.dd}"<br/>
    #user => "elastic"<br/>
    #password => "changeme"<br/>
  }<br/>
}<br/>
<br/> => 5044 port로 부터 입력을 받아서 ( filebeat ), elasticsearch로 보내준다 ( 9200 port ) <br/>

<h3>

<h2>3. 실행 방법</h2>
(설치폴더 bin)/logstash -f (설치폴더 conf)/my_pipeline.conf --config.reload.automatic<br/>
-f (path) 옵션 : config 파일위치 수동으로 지정<br/>
--config.reload.automatic 옵션 : 컨피그파일이 수정될때마다 자동으로 반영
