---
title: 'Windows Command 정리'
toc: true
toc_sticky: true
categories:
   - windows
   - os
last_modified_at: 2023-06-01T00:00:00-00:00
first_writed_at: 2023-06-01T00:00:00-00:00
subtitle: 명령어 정리
---


```shell
# 실행중인 프로세스
netstat -ano | findstr 8080 
# TCP       0.0.0.0:8080      0.0.0.0:0     LISTENING       43211
# TCP       [::]:8080         [::]:0        LISTENING       43211

# process id로 프로세스 이름
tasklist /FI "PID eq 43211"
# 이미지 이름        PID     세션이름    세션#     메모리사용
# ===============   ======  ==========  ======   ===========
# tomcat8.exe       43211   services        0       181,180K

# 프로세스 강제종료
taskkill /pid 43211 /f 
# 성공 : 프로세스(PID 43211)가 종료되었습니다.

```