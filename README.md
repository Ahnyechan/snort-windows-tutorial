# snort-windows-tutorial
snort-windows-tutorial

This tutorial is Snort Installation Tutorial in Security Monitoring class.
Snort is one of the IDS (Intrusion Detection System).


# Environment
- OS : Windows 7 32bit 
- snort 2.9.2.3 version
- Wincap
- APMsetup 7
- ADOdb(ActiveX Data Object Database)
- BASE(Basic Analysis and Security Engine)

# Install order

## (1) Install Wincap 

## (2) Install APMsetup7 



## (3) Install snort 2.9.2.3

Checking Snort this path C://

## (4) Install Adodb


After downloading, extract it to the folder where PHP is running
    
    C: \ APM_Setup \ htdocs \
    
Paste in this path


## (5) DB Setting

    C:\APM_Setup\Server\MySQL5\bin>mysqladmin -u root -p create snort

    C:\APM_Setup\Server\MySQL5\bin>mysql -D snort -u root -p < C:\Snort\schemas\create_mysql



    C:\APM_Setup\Server\MySQL5\bin>mysqladmin -u root -p create snort_base

    C:\APM_Setup\Server\MySQL5\bin>mysql -u root -p snort-base < C:\APM_Setup\htdocs\base\sql\create_base_tbls_mysql.sql

    C:\APM_Setup\Server\MySQL5\bin>mysql -u root -p snort_base < C:\Snort\schemas\create_mysql


    
Confirm DB creation
    
    C:\APM_Setup\Server\MySQL5\bin>mysql -D snort -u root -p

    mysql> show tables;
    +------------------+
    | Tables_in_snort  |
    +------------------+
    | data             |
    | detail           |
    | encoding         |
    | event            |
    | icmphdr          |
    | iphdr            |
    | opt              |
    | reference        |
    | reference_system |
    | schema           |
    | sensor           |
    | sig_class        |
    | sig_reference    |
    | signature        |
    | tcphdr           |
    | udphdr           |
    +------------------+
    16 rows in set (0.00 sec)
    
    
 ## (6) Install BASE
 
 After downloading, paste it into 
    
    C: \ APM_Setup \ htdocs \
    
 
 ## (7) Configuration Monitoring Webpage
 
 설치한 경로로 접속하면 BASE 설정을 할 수 있다. 
 127.0.0.1/base 접속
 
 
1) Step 1

Continue 클릭



2) Step 2

언어는 한글이 안되므로 English
Path toADODB는 앞서 설치한 ADODB의 경로를 적어준다. C:\APM_Setup\htdocs\adodb5


3) Step 3

- Pick a Database type는 MySQL을 선택한다.
- Database Name 은 앞서 생성한 DB이름을 넣어준다. 필자는 snort_base
- Database Host 는 localhost 를 적어준다.
- User Name 과 Password 는 DB의 ID와 PW를 넣어준다.
- Archive Database를 설정할 필요 없다.



 

4) Step 4
- Check 후 Base에서 접속 때 사용할 ID 와 PW를 적어준다. (필요하지 않으면 사용하지 않아도 됨)

Step 5 넘어가기 전에 base_action.inc.php 를 수정해 준다.
경로 : base\includes\base_action.inc.php
아래 부분은 Report 부분을 Mail로 보내주는 부분인데 파일이 없어서 오류가 난다. 그렇기 때문에 우선 주석 처리 해놓자. 


    include_once("$BASE_path/base_ag_common.php");
    include_once("$BASE_path/includes/base_constants.inc.php");
    //include_once("Mail.php"); // r.rioux added for PEAR::Mail
    //include_once("Mail/mime.php"); //r.rioux added for PEAR::Mail attachments


5) Step 5

Create BASE AG 를 클릭하면 미리 Table을 등록해 뒀기 때문에 DONE 이 표시 된다.
(Base DB 넣는 과정을 하지 않으면 이 부분에서 추가 된다)


6) Step 6 
Step 4에서 관리자 id 와 passwd를 설정 했으므로 id와 passwd 를 넣고 로그인 한다.

 

7) index 화면
 
 
 
 
