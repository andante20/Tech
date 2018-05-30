# 스파크 윈도우 설정

1. Scala 기반  
- JDK 8 다운로드 및 설치
  http://www.oracle.com/technetwork/java/javase/downloads  
  d:\opt\Java\jdk1.8.0_101  
  
- Linux Command Util 다운로드  
  https://github.com/bmatzelle/gow/releases/download/v0.8.0/Gow-0.8.0.exe  
  d:\opt\Gow

- SPARK 다운로드 및 압축해제
  https://www.apache.org/dyn/closer.lua/spark/spark-2.3.0/spark-2.3.0-bin-hadoop2.7.tgz

- 환경변수 설정  
  * JAVA_HOME=d:\opt\Java\jdk1.8.0_101
  * HADOOP_HOME=d:\opt\spark\spark-2.3.0-bin-hadoop2.7
  * SPARK_HOME=d:\opt\spark\spark-2.3.0-bin-hadoop2.7
  * PATH=%PATH%;%SPARK_HOME%\bin;%SPARK_HOME%\sbin
			
- Winutils 다운로드 및 복사  
  cd %SPARK_HOME%\bin
  curl -k -L -o winutils.exe https://github.com/steveloughran/winutils/raw/master/hadoop-2.7.1/bin/winutils.exe
		
```sh		
> spark-shell
scala> sc.setLogLevel("WARN")
scala> val f =  val f = sc.textFile("file:///d:/opt/spark-2.3.0-bin-hadoop2.7/readme.md")
scala> f.count
scala> f.first
scala> f.collect
scala> :quit
```

2. Python 기반
- JDK 8 다운로드 및 설치
- Linux Command Util 다운로드  
- SPARK 다운로드 및 압축해제
- 환경변수 설정
- Anaconda 설치 http://dwfox.tistory.com/67


- 환경변수 설정(관리자 콘솔)  
  setx -m : 시스템 환경변수 설정
  set     : 사용자별 환경변수 설정

```sh
setx -m JAVA_HOME=d:\opt\Java\jdk1.8.0_101
setx -m HADOOP_HOME=d:\opt\spark\spark-2.3.0-bin-hadoop2.7
setx -m SPARK_HOME=d:\opt\spark\spark-2.3.0-bin-hadoop2.7
setx -m PATH=%PATH%;%SPARK_HOME%\bin;%SPARK_HOME%\sbin
setx -m PYSPARK_DRIVER_PYTHON ipython
setx -m PYSPARK_DRIVER_PYTHON_OPTS notebook
```

```sh
> pyspark --master local[*]
```

### 참고
---
* Jake 설치 파일