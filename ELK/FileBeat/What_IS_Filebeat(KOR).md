<h1>File Beat</h1>
log 파일을 지켜보다가 이벤트가 발생했을때,
마지막으로 체크한 위치 이후 부분을 Elastic Search 혹은 Logstash로 보낸다. 
<hr/>
<h2>왜 사용 하는가? </h2> 
1) 시스템이 중단되는 경우, 중단 점이 기록되어 있기 때문에 누락없이 로그를 수집할 수 있다. (Harvester)
 <h4>[Harvester] 마지막으로 로그를 보냈던 지점을 기억하여, 새 로그데이터가 쌓이면 해당 로그만 전송해줌</h4>
2) Logstash로 로그를 수집할 때는, 데이터 처리 및 수집을 해야하기 때문에 성능 이슈가 발생할 수 있다. <br/>
&nbsp;&nbsp;&nbsp;2-1) FileBeat는 Logstash에 비해 가볍고, Logstash 성능에 따라 속도를 조절함.<br/>

<h2> Filebeat 설정해야할 부분 </h2>
1) Log file Path<br/>
2) Output Line

<h2> ※ KAFKA </h2>
ELK 스택에서 많이 사용하는 메시지 분산 시스템 https://soft.plusblog.co.kr/3<br/>

특징으로는, <br/>
1) 메시지를 메모리가 아닌, 파일 시스템을 사용하여 저장함<br/>
1-1) 파일시스템은 속도가 느리다는 단점이 있으나, H/W의 발달로 인한 속도 향상<br/>
1-2) 메시지를 파일시스템으로 보관하여, 영속성을 지님.<br/>
2) 관리의 용이성
2-1) 유동적인 트래픽 대처하기 좋고, 각 Beat에 들어가서 관리할 필요가 없다.<br/>
2-2) 다중 Producer / Client 구조의 경우, 용도에 맞게 구분하여 필요로그만 사용
