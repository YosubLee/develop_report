## Linux

## 유용한 명령어
* gid(group id) : 5001, uid(user id) : 5001 번의 *bash 권한을 소유한* test 그룹 및 유저 생성후 `/home/testtest`를 생성된 유저의 홈디렉토리로 사용한다.
````
groupadd -g 5001 test && useradd -u 5001 -g 5001 -d /home/testtest -m test
````
* 생성이후 유저 및 그룹 확인 (경로 : `/etc/passwd`)
````
test:x:5001:5001::/home/testtest:/bin/bash
````
* 생성 이후 권한 : 생성된 유저 및 그룹 권한의 rwx권한만 부여되고 그룹 및 other의 권한은 부여되지 않음
````
drwx------ test test /home/testtest
````
