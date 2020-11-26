## Linux (Cent OS)

### CentOS Release Version
* `/etc/centos-release` 파일 

````bash
cat /etc/centos-release

CentOS Linux release 8.2.2004 (Core)
````
### 폴더 구조
* `/` (Root) : 최상위 폴더
* `/bin` : 시스템에서 사용되는 기본 명령어 (cp, mv ..)
* `/sbin` : 시스템 관리자가 사용하는 명령어 (reboot, shutdown)
* `/etc` : 시스템 설정 파일들 보관 
* `/var` : 시스템의 대부분의 Log 저장
* `/proc` : 시스템 각종 프로세서, 프로그램 정보, 하드웨어 정보 
    * 물리적으로 디스크에 저장하지 않음 (메모리에 저장)
* `/home` : 일반 사용자들이 사용하는 디렉토리
* 

### UID, GID
* gid(group id) : 5001, uid(user id) : 5001 번의 *bash 권한을 소유한* test 그룹 및 유저 생성후 `/home/testtest`를 생성된 유저의 홈디렉토리로 사용한다.
````
groupadd -g 5001 test && useradd -u 5001 -g 5001 -d /home/testtest -m test
````
* 생성이후 유저 및 그룹 확인 (경로 : `/etc/passwd`)
````
test:x:5001:5001::/home/testtest:/bin/bash
````
* 생성 이후 권한 : 생성된 user의 rwx권한만 부여, group 및 others에게는 아무 권한도 부여되지 않음.
````
drwx------ test test /home/testtest
````
