<h3>LogStash config File Setting</h3>

- 1 Input Setting<br/>
=========== fileBeat input ========== <br/>
input {<br/>
　beats {<br/>
 　　port => 5044<br/>
　}<br/>
}<br/>
=============================== <br/>
// This is because the output-Logstash port is set to 5044 in the filebeat configuration.(default)<br/>

- 2 Output Setting<br/>
=========== Elastic Search output ========== <br/>
output {<br/>
　elasticsearch {<br/>
 　　hosts => ["http://localhost:9200"]<br/>
  　　index => "%{[@metadata][beat]}-%{[@metadata][version]}-%{+YYYY.MM.dd}"<br/>
　}<br/>
}<br/>
// the Elastic Search port is set to 9200.(default)<br/>

================== Full .conf file ================= <br/>

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
　}<br/>
}<br/>

=============================== <br/>

If you are running a file bit,<br/>
the data file will be sent to the log stashes,<br/>
which will filter the data and send it to Elastic Search.<br/>

If you want to Test Logstash,<br/>
change output setting to <br/>
<br/>
output {<br/>
　elasticsearch {<br/>
 　　stdout { codec => rubydebug }<br/>
　}<br/>
}<br/>

then, output is printed to console.
