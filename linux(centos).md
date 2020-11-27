# 목차
* [Directory Structure](#DirectoryStructure)
* [File](#File)


### Directory Structure
* `/` (Root) : 최상위 디렉토리
* `/bin` : 시스템에서 사용되는 기본 명령어 (cp, mv ..)
* `/sbin` : 시스템 관리자가 사용하는 명령어 (reboot, shutdown)
* `/etc` : 시스템 설정 파일들 보관 
* `/var` : 시스템의 대부분의 Log 저장
* `/proc` : 시스템 각종 프로세서, 프로그램 정보, 하드웨어 정보 
    * 물리적으로 디스크에 저장하지 않음 (메모리에 저장)
* `/home` : 일반 사용자들이 사용하는 디렉토리

#### File
##### `/etc` 하위 디렉토리
* `/etc/centos-release` 
````bash
cat /etc/centos-release
#######################

CentOS Linux release 8.2.2004 (Core)
````

##### `/proc` 하위 디렉토리 
* `/proc/cpuinfo` 
````bash
cat /proc/cpuinfo
#######################

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 158
model name      : Intel(R) Core(TM) i3-8100 CPU @ 3.60GHz
stepping        : 11
microcode       : 0xd6
cpu MHz         : 3600.600
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 22
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d
bugs            : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
bogomips        : 7200.00
clflush size    : 64
cache_alignment : 64
address sizes   : 39 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 158
model name      : Intel(R) Core(TM) i3-8100 CPU @ 3.60GHz
stepping        : 11
microcode       : 0xd6
cpu MHz         : 3603.048
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 4
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 22
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb                                                                                 rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx                                                                                 est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fau                                                                                lt invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clf                                                                                lushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d
bugs            : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
bogomips        : 7200.00
clflush size    : 64
cache_alignment : 64
address sizes   : 39 bits physical, 48 bits virtual
power management:

````
* processor : Cpu Core (CPU 전체 Core 갯수 명령어 : `grep -c processor /proc/cpuinfo`)
* physical id : 물리적인 CPU ID (processor가 달라도 physical id가 동일하다면 물리적으로 같은 CPU의 다른 코어)

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