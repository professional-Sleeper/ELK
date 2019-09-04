<h1> Setting </h1>
<h2> open filebeat.yml </h2>
<h3> 1. find Filebeat input.</h3>
change path (real log path) ex:)  D:\ELK\log\logstash-tutorial.log\*
<h3> 2. find Elastic/Logstash output </h3>
It depends on what architecture you have.<br/>
Delete the '#' of the output to use.<br/>
* If you want change output ip, modify hosts. defualt ( Elastic : 9200 , Logstash : 5044 )
<h2> go modules.d folder </h2>
remove disabled from filename that you want use.

<h1>1. cd FileBeat Path (with administor auth) </h1>
<h3>1-1 ./filebeat.exe -e -c filebeat.yml </h3>
* -e means debug mode. exectue foreground and output is written to console.<br/>
* -c means config. you apply filebeat.yml file while executing.<br/>
<h3>1-2 You can modify Ip adress and Port in elasticsearch.yml (config folder)
