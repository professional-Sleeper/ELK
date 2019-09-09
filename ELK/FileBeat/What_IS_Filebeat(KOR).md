<h1>File Beat</h1>
log 파일을 지켜보다가 이벤트가 발생했을때,
마지막으로 체크한 위치 이후 부분을 Elastic Search 혹은 Logstash로 보낸다. 
<hr/>
<h2>왜 사용 하는가? </h2> 
1) 시스템이 중단되는 경우, 중단 점이 기록되어 있기 때문에 누락없이 로그를 수집할 수 있다.<br/>
2) Logstash로 로그를 수집할 때는, 데이터 처리 및 수집을 해야하기 때문에 성능 이슈가 발생할 수 있다. <br/>
&nbsp;&nbsp;&nbsp;2-1) FileBeat는 Logstash에 비해 가볍고, Logstash 성능에 따라 속도를 조절함.
