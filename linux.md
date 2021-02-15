<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210214220630959.png" alt="image-20210214220630959" style="zoom:50%;" /> 

운영체제 : 하드웨어를 관리, 제어 해주는 역할을 한다.( + 이런 하드웨어를 편리하게 다룰수있게 사용자에게 유저인터페이스를 제공해준다.)



### 리눅스 개발

리누스 토발즈 라는 대학생이 GNU시스템에 적합한 커널을 개발



<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210214222244447.png" alt="image-20210214222244447" style="zoom:50%;" /> 

shell?

:  간단히 말해서 명령어 치는 프로그램을 말한다.( ex> cmd ) 여기서 우리가 내리는 명령어를 치고,(폴더를 이동,폴더를 만들어라, 폴더를 삭제해라.) 그러면 그 명령어를 커널이 알아들을수있는 형태로 번역해서 커널한테 전달한다. 그래서 쉘을 다른말로 명령어를 실행시켜주는 프로그램이라는 의미로 '명령어 번역기' 라고도 말한다.

 참고로 명령어들은 다 실행하는 프로그램이다. 그래서 system에 들어가서 확인해보면 ipconfig명령어에 대한 ipconfig.exe라는 프로그램이 존재한다.

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210214222648089.png" alt="image-20210214222648089" style="zoom:67%;" /> 

`#` : 권한 같은걸 의미한다.

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210214222742645.png" alt="image-20210214222742645" style="zoom:67%;" /> 

커널?

: 운영체제의 핵심부분이다.  하드웨어를 관리해주고 사용자가 실행한 명령어(예를 들어, 윈도우로 쳤을때 파일을 더블클릭했다라는 명령어)를 하드웨어한테까지 전달해서 알려주는 일을 한다.



리눅스 기본명령어

~~~shell
#현재 내 터미널이 가르키고 있는 위치
pwd

#명령프롬프트에서의 #과 $
$은 일반사용자를 의미
'#'은 관리자 계정을 뜻한다.

#관리자계정으로 변경하기
sudo -s
su - root

#특정명령어의 사용법보기
man 명령어
ex> man ls
(내용을 확인할때 엔터를 치면 한줄씩, 스페이스를 누르면 한페이지씩 넘어간다. 끄고 싶으면 q입력.)
~~~



### 디렉토리 관련 명령어

####  ls 명령어

~~~shell
#pwd : 현재 작업 디렉토리 확인 
#cd : 작업 디렉토리 변경
#ls : 디렉토리 내용확인
참고> 파일이름앞에 .~~ 처럼 .이 있으면 숨긴파일임을 나타내는것이다.
그리고 이름목차중에서 파란색으로 뜨는것은 파일이고 기본색인것들은 파일을 의미한다.
ls -a : .과 ..이랑 숨긴파일도 같이 나온다.
ls -l : 파일,디렉토리의 자세한 정보까지 출력한다.

ls -al : a옵션과 l옵션의 내용이 합쳐서 출력된다.

-R옵션 : 하위디렉토리의 경로까지 전부다 출력해준다.
-F옵션 : 파일과 디렉토리를 구분해준다.( 근데 요즘버젼은 ls만해도 색깔로 구분된다.
근데 강사의 경우 ls -al로 해서 권한부분내용에서 맨앞에 d가 있으면 디렉토리고 -이면 파일이여서 이걸로 구분한다고 한다.)

ls -al /kjy : 특정디렉토리안의 정보를 보여준다.
ls -ld /kjy : 특정디렉토리의 안이 아니라 그 디렉토리자체의 정보를 보여준다.(d옵션의 역할임)

~~~





<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215003943405.png" alt="image-20210215003943405" style="zoom:67%;" />

하드링크와 비슷한개념으로 윈도우에 심볼릭링크라는 개념이 있다. 그것의 의미는 윈도우의 단축아이콘이라고 생각하면 된다. 그래서 여기서 간단히만 설명하면 해당파일의 단축아이콘 갯수라고 생각하면 된다.(정확한 개념은 아니다. 나중에 배울것임)

#### 디렉토리 만들기

~~~shell
mkdir /test
하위구조도 함께 만들려면 -p 옵션을 함께사용한다.
예> mkdir -p /test/test/test
mkdir a b c : 디렉토리 3개 a,b,c를 동시에 만든다.
~~~



#### 디렉토리 삭제

~~~shell

#rmdir [삭제할 디렉토리 이름]: 지우려는 폴더내부에 특정파일이나 디렉토리가 있으면 안지워진다. 쉽게 말해 빈디렉토리만 삭제가능하다.
#rm -r [삭제할 디렉토리 이름] : 폴더안에 자료가 있어도 통째로 지워진다.

#rm -rf [삭제할 디렉토리 또는 파일] : 삭제하려는 대상을 디렉토리던 폴더던 한꺼번에 완전히 지운다. (f옵션때문에 파일을 지우는것이고 r옵션때문에 내용이들어있는 디렉토리도 같이 지워진다..?)
ex> rm -rf /test
#rm -rf ./* : 현재디렉토리안에 있는 모든 내용을 삭제한다. 그리고 현재디렉토리자체는 살아있다.(*이 모든 내용을 의미한다.)

~~~



#### 디렉토리 이동

~~~shell
-절대경로와 상대경로 방식이 있다.
절대경로 : 최상위디렉토리인 /에서부터 특정파일 또는 디렉토리의 경로를 모두입력.
상대경로 : 현재 작업디렉토리를 기준으로 특정파일 또는 디렉토리의 경로를 입력.
#상대경로에서 알아둘 명령어들
. : 현재디렉토리를 의미
.. 또는 ../ : 바로 위의 상위디렉토리
#cd [이동할 위치경로]

#현재위치를 나타낼때 맨처음이 / 로 시작하면 절대경로다!
예> /etc/sysconfig : 절대경로 (여기서 /를 루트디렉토리라고 말한다. 즉, 최상위디렉토리에서 etc라는 폴더 밑에 sysconfig를 의미한다.)
	etc/sysconfig : 상대경로

~~~



#### 루트디렉토리?

~~~shell
# 리눅스에서 루트디렉토리의 종류는 3가지다.
/ : 최상위디렉토리 (내 맥의 경우 var이 최상위디렉토리다.)
root : 사용자계정
root : 사용자의 홈디렉토리가 root디렉토리가 된다. 다시말해서, 최상위디렉토리root계정 바로 밑에 root디렉토리가 하나 더 만들어져있다. ( /root 이 안에서 우리가 작업을 하는것이다.)
~~~



#### 디렉토리 이동 또는 이름을 변경

~~~shell
#mv [현재디렉토리이름 또는 위치] [변경하게될 디렉토리이름 또는 위치]


~~~



#### 디렉토리또는 파일 복사

~~~shell
#빈디렉토리가 아니라 내용이 들어있는 디렉토리를 통째로 지우거나 복사할때는 -r 옵션을 붙여라!!
cp -r [원본경로] [이동할경로]
예> cp /kjy /kjy2


~~~



### 파일관련 명령어

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215015510061.png" alt="image-20210215015510061" style="zoom:67%;" /> 



#### <img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215015809834.png" alt="image-20210215015809834" style="zoom:67%;" /> 

#### 

#### cat

~~~shell
#head를 이용할때 현역에서 자주쓰는 방법
cat [보려는파일경로] | head
#head뒤에 옵션을 줘서 보여주는 줄수를 정할수있다.
cat [보려는파일경로] | head -5

~~~



#### more

~~~shell
#more [파일경로]
참고> 내용을 출력해서 볼때 내용이 긴 상태에서 다음줄로 이동할때는 엔터, 나가려면 q를 누른다.
~~~



####  tail

~~~shell
#tail에서 자주 쓰는 -f옵션.
-f옵션을 쓰면은 결과를 출력할때 프롬프트를 안보여주면서 출력한다.\


참고> tail -f /var/log/messages를 해주게되면은 실시간으로 로그내용을 확인..?(나중에 알려줄꺼임)
~~~



-----------

### 문서편집기

: 리눅스로 파일같은걸 만들고 그 파일에 대한 내용을 편집해야 할것이다. 그때쓰게되는 대표적인 편집기들을 살펴보자.





#### vi편집기

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215021925098.png" alt="image-20210215021925098" style="zoom:67%;" />

:vi편집기는  3가지 모드가 있다!

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215022020768.png" alt="image-20210215022020768" style="zoom:67%;" /> 

커서를 이동할때는 '명령모드'에서 해야한다.



i,a,o는 각각 편집모드로 넘어갈때 커서의 위치가 다르다.

##### 

##### command모드

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215022649273.png" alt="image-20210215022649273" style="zoom:67%;" />

(이것 말고도 많음.)

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215023025137.png" alt="image-20210215023025137" style="zoom:67%;" /> 

>삭제되거나 했을때 '되돌리기'는 u를 누른다!!
>
>커서를 이동하면서 커서위치한곳만 값을 바꾸고 싶을때 r을 누르고 바꾸고싶은값을 입력한다!!
>
>참고> '(2)삭제'는 사실은 '삭제'가 아니라 '잘라내기'의 개념이다.



##### d[커서이동] 의 내용

~~~shell
#숫자누르고dd : 숫자칸만큼 삭제된다.
d를 누르고 G를 누르면 d를 누른위치부터 가장 맨 마지막줄까지 삭제되고,
d를 누르고 w를 누르면 d를 누른위치부터 한단어만큼 삭제된다.
이런식으로 응용해서 활용한다.
~~~

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215023603282.png" alt="image-20210215023603282" style="zoom:67%;" />

~~~shell
#현재 커서가 위치한곳포함해서 아래로 여러줄을 복사하기!
: 숫자누르고 yy를 한다!!
~~~



##### edit모드

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215023735734.png" alt="image-20210215023735734" style="zoom:67%;" /> 



##### Last Line모드

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215023803253.png" alt="image-20210215023803253" style="zoom:67%;" />

참고>'(2)검색 및 반환' 내용에서 한꺼번에 바꾸고 싶지않으면 /g를 뺀다.

##### 내용을 변경하기

~~~
:%s/[바꾸고싶은내용]/[바뀐내용]
~~~



<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215024047888.png" alt="image-20210215024047888" style="zoom:67%;" /> 

참고> !는 '강제'를 의미한다.



#### nano편집기

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215030151612.png" alt="image-20210215030151612" style="zoom:67%;" />![image-20210215030219111](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215030219111.png) 

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215030219111.png" alt="image-20210215030219111" /> 

 

![image-20210215030339291](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215030339291.png) 

![image-20210215030458542](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215030458542.png)

![image-20210215030526984](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215030526984.png)





----------

### 파일검색 - grep이론

![image-20210215031000755](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215031000755.png)

![image-20210215031040614](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215031040614.png) 

-i옵션 : 대소문자를 구분하지말고 찾으라는 의미다.

<img src="C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215031156115.png" alt="image-20210215031156115" style="zoom:67%;" />

-w옵션은 단어가 완전히 일치한것만 찾는다.

![image-20210215031348364](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215031348364.png)

r* 의 의미 : r로 시작하는 모든 단어들

r.의 의미 : r다음에 한문자만 오는경우의 단어

[abc]oot의 의미 : aoot , boot, coot가 이것에 해당되는 단어가 된다.

[a-d]oot의 의미 : a부터 d까지라는 의미로, aoot,boot,coot,doot까지 출력된다.

[1-5]oot의 의미 : 1부터 5까지라는 의미로, 1oot,2oot,3oot,4oot,5oot까지 출력된다.

[a-c,g-h]oot의 의미 : aoot,boot,coot, goot,hoot들이 출력된다.

~~~
grep [a-c,g-h]oot[2-8] ./test과 같은 코드 = 
grep [a-c,g-h]oot ./test | grep root[2-8]
~~~





![image-20210215031735983](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215031735983.png) 



### 디렉토리검색 - find이론

![image-20210215033115708](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215033115708.png)

-exec rm -rf부분이 [행동]을 의미하는데 행동을 따로 지정하지않으면 여기에 print라는 [행동]이 default값이 있는것이다. 

![image-20210215080242732](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215080242732.png)

![image-20210215080532120](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215080532120.png)

~~~
예>
find / -name [내가검색할이름]: 최상위디렉토리를 경로로 지정해서 시스템전체에서 한번 찾겠다 라는 의미고 -name을 넣음으로서, 시스템전체에서 이름으로 검색하겠다 라는 의미다.
find / -name [내가검색할이름] -type f : 시스템전체에서 이름을 검색하는데 file만 찾겠다 라는 의미다.
find / -size +100M :시스템전체에서 (+)는 이상을 의미함으로써, 100Mbyte이상인것을 찾는다.
find ./ -name test -ls: 현재위치에서 이름이 test인것을 자세하게(-ls)하게 찾는다.
find ./ -name test -exec rm -rf {} \; : 현재위치에서 이름이 test인파일들을 삭제한다.
~~~





-------------

### 하드링크와 심볼릭링크

![image-20210215082014569](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215082014569.png)

![image-20210215082106188](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215082106188.png)

하드링크란? 극단적으로 이야기하면은 우리눈에 보이는 파일들 자체가 하드링크다.

운영체제 설명할때 운영체제의 역할은 하드웨어를 제어하기도하고 사용자에게 편리한 인터페이스를 제공한다. 하드디스크에서 물리적인 부분의 판을 본다고해서 어디에 뭐가 저장되어있는지 알수가 없을것이다. 그것을 우리 눈에 보이게 보여주는일을 해주는게 운영체제인데, 운영체제는 이 링크라는 개념에 의해 우리 눈에 보여지는것이다. 

포맷이라는것은 '파일시스템'을 새로 생성하는것이고 이걸 새로 생성하기때문에 링크가 없어지는것이다.

![image-20210215082445466](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215082445466.png)

하드링크는 특정파일 또는 디렉토리에 직접적으로 접근할수있도록 그 하드디스크상의 위치를 가리키는 파일이다.

![image-20210215082823243](.\linux_pic\link)

심볼릭링크는 윈도우에서 바로가기 아이콘이랑 비슷한 개념이다. 하드디스크는 디스크상의 파일을 직접가리켰다면 심볼릭링크는 간접적으로 한번 거쳐서 가리킨다.

우리가 눈으로 보는것은 '링크'다. 

파일시스템을 배우면은 'i-node'라는것을 배우는데, 디스크상의 주소라고 생각하면 된다.

이 파일들이 하드링크일때 전부다 i-node의 주소가 같다.

![image-20210215083716189](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215083716189.png)



##### 하드링크만들기

~~~shell
vi origin 이라는 파일을 만들어서 편집기로 안에 내용을 작성해놓고,
ls -l로 확인하게되면,
-rw-r--r--. 1 root root 4 Feb 14 23:33 origin 이라고 뜨는데 여기서 1이 하드링크의 수를 의미한다.
#하드링크를 생성
ln origin origin_hl: 옵션없이 origin파일을 지정하고 하드링크이름은 origin_hl로 해서 생성한다.
이런후에 ls -l을 하게 되면
-rw-r--r--. 2 root root 4 Feb 14 23:33 origin
-rw-r--r--. 2 root root 4 Feb 14 23:33 origin_hl
숫자가 2로 늘어나있다.
그리고 난후에 vi편집기로 origin의 내용만 수정해서 추가해도
cat origin해서 보이는 값과 cat origin_hl해서 보이는 값이 같다!!
(i-node를 확인하는 옵션-i를 붙여서 ls -il로 확인하게되면 둘다 i-node값이 같음)\

반면에 cp를 이용해서 복사했을때는,
cp origin origin_cp
ls -il
17983618 -rw-r--r--. 2 root root 4 Feb 14 23:33 origin
17983616 -rw-r--r--. 1 root root 4 Feb 14 23:33 origin_cp
17983618 -rw-r--r--. 2 root root 4 Feb 14 23:33 origin_hl
origin_cp의 i-node값은 다르다.

~~~

![image-20210215084941690](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215084941690.png) 

##### 심볼릭링크만들기

~~~shell
#심볼릭링크 상대경로로 만들기
ln -s origin origin_sl
ls -il
17983618 -rw-r--r--. 2 root root 4 Feb 14 23:33 origin
17983616 -rw-r--r--. 1 root root 4 Feb 14 23:33 origin_cp
17983618 -rw-r--r--. 2 root root 4 Feb 14 23:33 origin_hl
17983619 lrwxrwxrwx. 1 root root 4 Feb 14 23:33 origin_sl->origin  //상대경로로 출력
심볼리릭 링크는 i-node값이 다르게 생성되고 파일이름origin_sl이 화살표로 원본파일을 가리키게 출력된다.

#심볼릭링크 절대경로로 만들기
ln -s /kjy/origin /kjy/origin_sl2
ls -il
17983631 lrwxrwxrwx. 1 root root 4 Feb 14 23:33 origin_sl2-> /kjy/origin
//가리키는 결과가 다르게 나온다.

#상대경로로 만든것과 절대경로로 만든것의 결정적 차이점!!
만약에 심볼릭링크를 mv시키게 된다면
mv origin_sl /root/
mv origin_sl2 /root/
cd /root/
//root위치에서도 ls -il의 결과로 가리키는 위치가 위처럼 상대경로는 그대로 origin_sl->origin]
이라고 나오고 절대경로는 origin_sl2-> /kjy/origin라고 나오기때문에 절대경로는 원본파일을 잘 찾아가지만 상대경로는 못찾아갈것이다.


~~~



##### 만약 원본origin이 삭제가 된다면?

~~~
rm -rf origin
ls -il
17983616 -rw-r--r--. 1 root root 4 Feb 14 23:33 origin_cp
17983618 -rw-r--r--. 1 root root 4 Feb 14 23:33 origin_hl
17983619 lrwxrwxrwx. 1 root root 4 Feb 14 23:33 origin_sl->origin
cat origin_sl
cat: origin_sl : No such file or directory
cat origin_hl
kjy
123
456
789
하드링크로 출력할때는 내용이 잘 나온다.
~~~





----

### 권한의 이해와 설정방법

![image-20210215090808590](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215090808590.png)

![image-20210215090847178](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215090847178.png)

권한도 파일시스템상에 존재한다.

![image-20210215091010796](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215091010796.png)

~~~
drwxr-xr--. 에서 .을 빼고 10개문자로 되어있다.
맨첫번째문자d를 빼고 9개문자가 권한을 나타낸다. 문처음의 d는 파일인지 d디렉토리인지 알려주는것이다.
9개의 문자를 3개씩 자를수있다.
rwx / r-x / r-- 로 구분되는것이다.
소유자는 3번째필드에 누구인지 보여준다. (여기서는 root)
관리그룹은 4번째필드를 의미한다.


~~~

![image-20210215091322246](C:\Users\kjy59\Desktop\study\linux\linux_pic\permission)

~~~
위 이미지에서,
root사용자가 아니면 소유자가 아니기때문에 '소유자권한'쪽을 부여받지 못한다.
만약에 내가 abc라는 애면, root라는 '관리그룹'에 속해있기때문에 관리그룹 권한을 부여 받을것이다.
그리고 kjy라는 애면, 어느 그룹에도 속해있지 않기때문에 '나미저권한'부분만 권한을 부여 받을것이다.
---------------------------------------------------------------------------------
예외!!>루트root사용자이면 소유자가 아니고 권한그룹에 속해있지않다고 하더라도 얼마든지 사용가능하고 접근이 가능하다!!
~~~



#### 권한설정 방법

![image-20210215092059470](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215092059470.png)

일반적으로 [권한]은 '옥텟모드'를 많이 쓴다.

![image-20210215092149715](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215092149715.png)

만약에 전부다!! 주고 싶으면?

~~~
chmod a file 이라고 한다.
~~~

![image-20210215092241314](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215092241314.png)

![image-20210215092420811](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215092420811.png)

umask라는게 기본적으로 022로 설정되어있어서 파일과 디렉토리를 만들때 기본값이 위처럼 기본적으로 설정되어있다. 

기본권한의 숫자 의미는

dir       777

file       666

umask 022

라고 했을때 각각의 값에서 umask값을 and연산을 하면 위의 '기본권한'에 나타나는 숫자가 나온다.

![image-20210215093224185](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215093224185.png)

##### 실습할 내용(22강)

![image-20210215093318212](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215093318212.png)

umask확인하기

~~~
umask
~~~



파일같은경우에는,

~~~
처음에 파일을 생성할때,
echo test > file2
이런식으로 파일을 생성과 동시에 내용을 입력했는데 어떤내용이 있는지도 알수없는 상태에서 파일을 실행하게되면 위험할수있기때문에 파일들의 경우에 기본권한값으로 '실행'내용은 부여받지 못하게 되어있다. 그래서 안전하다고 판단될때 관리자가 실행권한을 부여해줘야 그 이후 실행이 가능해진다.

~~~



#### 심볼릭모드

##### 권한뺏기

~~~shell
chmod o-r file
//나머지사용자에게 '읽기권한'을 뺀다.
ls 0l
-rwxw----. 1 root root 0 Feb 14 23:44
~~~



#### 옥텟모드

##### 권한바꾸기

~~~shell
chmod  640 dir
drw-r-----. 1 root root 0 Feb 14 23:44
~~~

![image-20210215094530441](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215094530441.png) 

![image-20210215095211907](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215095211907.png) 

파일을 읽을수있으려면 최소한! r권한이 있어야한다.

~~~shell
#쓰기권한만 준상태일때, ( x  △  x )
편집으로 쓰고 나서 강제로 :w! 저장하게되면은
쓴게 반영된다.
~~~



--------------

### 특수 권한

![image-20210215095644189](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215095644189.png)

![image-20210215095907564](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215095907564.png) ![image-20210215100103645](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215100103645.png)

![image-20210215100214517](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215100214517.png)



##### 특수권한 실습내용

![image-20210215100300733](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215100300733.png) 

#### stickBit  권한 주기

~~~shell
chmod 1777 file
ls -l
-rwxrwxrwt. ~~~
~~~



참고> 사용자의 패스워드 저장내용페이지

~~~
ls 0l /etc/shadow
ls 0l /etc/shadow
----------.  ~~
// 이 파일에 대해서 누구도 권한이 없다.
(추가 내용은 나중에 다시 들어서 필기하기)
~~~



### Shell

![image-20210215102123310](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215102123310.png)

(방향재지정 메타문자가 중요함)

![image-20210215102226559](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215102226559.png)

![image-20210215102253473](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215102253473.png)

명령어 히스토리 : 지금까지 친 명령어기억.

쉘 스크립트 : 명령어프로그램을 짜는것.

~~~
echo $SHELL
//$를 붙이면 그뒤에 오는 문자를 '변수'로 판단하게 한다.
~~~





#### 쉘 메타문자

![image-20210215102717455](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215102717455.png)

![image-20210215102741555](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215102741555.png) 

![image-20210215102818243](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215102818243.png)

파일이름이 띄어쓰기가 들어갔을때,

~~~shell
vi 'abc d'
~~~



#### <중요> 방향 재지정 메타문자

![image-20210215103144098](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215103144098.png)

![image-20210215103234090](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215103234090.png)

|의 예

~~~shell
grep root /etc/passwd
= cat etc/passwd | grep root
~~~

![image-20210215103654442](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215103654442.png)

### 사용자 초기화 파일

![image-20210215103744257](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215103744257.png) 

![image-20210215104017042](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215104017042.png) 

![image-20210215104250926](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215104250926.png)

### KSH쉘 사용해보기

(30강)



### 쉘명령어-환변변수 설정하기

.cshrc : c쉘의 초기화파일(러닝스크립트..?)

.bashrc : bash쉘의 초기화파일(러닝스크립트..?)

~~~sh
cat .bashrc
//를 확인해보면 여기에 alias가 설정되어있다.

~~~



### 쉘명령어-메타문자사용하기



~~~shell
echo ls -l
ls -l //그냥 출력
echo `ls -l`
​~~~// ls -l 명령어가 실행된다.

-------------------------------------
echo $PS1
\$
echo '$PS1'
$PS1 // $기능을 무시하게 되서 그냥 문자출력
echo "$PS1"
\$   // " ~"의 경우는 $기능은 무시하지않아서 PS1의 변수값출력

echo ' `ls` test'
`ls` test

echo "`ls` test"
amacpmda-ks.cfg
back.c
net_conf
syslog test //마지막에 test문자가 출력
echo "result of 'ls' `ls` immida"
result of 'ls' amacpmda-ks.cfg
back.c
net_conf
syslog immida
-------------------------------------
참고> 쉘프로그래밍은 윈도우에서도 할수있다! 윈도우에서 우리가 cmd에서 치는 명령어들로 짤수 있다.
윈도우에서는 쉘프로그래밍을 이렇게 안부르고 '배치파일','배치프로그래밍'이라고 부른다.


~~~



### 쉘 명령어 사용 - 방향재지정 메타문자 실습

~~~shell
cat file
test
echo qwer > ./file
cat file
qwer // > 1번만 쓰면 내용이 덮어쓰기 된다.
-------------------------------------
cat file
test
echo qwer >> ./file
cat file
test
qwer //>> 2번 썼기때문에 내용을 이어쓴다.

-------------------------------------
#짧게 보기위한 방법
ls -al /etc/ | more 
//첫번째부분명령어의 결과를 한페이지 단위로 끊어보기위해 more을 추가


ls -al /etc |grep rc | more
또는
ls -al /etc |grep rc | tail -5

-------------------------------------
cat passwd | grep sim
sim:x:1000:1000:sim:/home/sim:/bin/bash
#이 내용의 출력결과에서 열만 뽑으려면 cut이용
cat passwd | grep sim | cut -d":" -f6
/home/sim

참고> df -h //디스크의사용량을 표시
#df -h 응용
df -h | grep centos
/dev/mapper/centos-root 17G 4.1G 13G 24% /
~~~



### 프로세스 제어 - 이론

![image-20210215111733368](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215111733368.png)

윈도우에서 눈에 보이는곳(foreground) 동작하는 프로그램을 프로세스라고 부르고 background에서 동작하는 프로그램을 '서비스'라고 부른다.

![image-20210215112007828](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215112007828.png)

![image-20210215112100470](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215112100470.png)

운영체제(예>윈도우)가 다른 프로세스,프로그램을 실행시켜준다.

참고> 리눅스에서는 데몬프로세스개념이 중요하다.

~~~shell
sleep 20 & //&를 붙이면 백그라운드에서 돌린다.

ps -f

ps -ef | more

top //프로세스목록을 방향키로 왔다갔다하면서 볼수있게 뜬다.
~~~



#### 프로세스 종료

~~~shell
ps -ef | grep sleep

pkill -9 sleep
~~~



### 압축 및 아카이브 - 이론

![image-20210215115805359](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215115805359.png)

![image-20210215115903207](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215115903207.png) 

아카이브 : 파일저장용도로 사용된다.

![image-20210215120328295](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215120328295.png)

![image-20210215120603724](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215120603724.png) 

자바기반의 파일을 jar아카이브형식으로 묶은거다.

![image-20210215120645417](C:\Users\kjy59\AppData\Roaming\Typora\typora-user-images\image-20210215120645417.png)

아카이브는 압축이 아니다. 그래서 용량을 줄이기위해서는 압축도 따로 해야 한다.



### 아카이브 실습

~~~shell
tar cvf fruits.tar apple banana tomato
ls -l
-rw-r--r--. 1 root root     0 Feb 14 23:55 apple
-rw-r--r--. 1 root root     0 Feb 14 23:55 banana
-rw-r--r--. 1 root root 10240 Feb 14 23:55 fruits.tar
-rw-r--r--. 1 root root     0 Feb 14 23:55 tomato

주의사항> tar은

-------------------------------------------\
#압축하기
zip fruits.zip apple banana tomato

#gzip이나 bzip은 아카이브로 묶인걸 압축하는 애다.
gzip furits1.tar
==> fruits1.tar.gz
bzip2 fruits2.tar
==> fruits2.tar.bz2

#압축풀기
unzip fruits.zip

gunzip fruits2.tar.gz

#tar파일까지 한꺼번에 한꺼번에 압축풀기=>z옵션
tar zxvf frutis1.tar.gz //압축내용과 아카이브를 한번에 해제시킨다.
~~~

