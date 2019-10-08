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

<hr/>
* Exception Control<br/>
<img src="https://user-images.githubusercontent.com/44637739/66366794-9857c580-e9cc-11e9-8ff3-409d510bb1b3.png">
If you see this comment, It's path problem.<br/>
Program doesn't find my_fifeline.conf file, So This exception occured.<br/>
This case, You Should write full path.<br/>
ex )<br/>
D:/ELK/logstash-7.3.1/bin/logstash -f D:/ELK/logstash-7.3.1/bin/my_pipeline.conf --config.reload.automatic
