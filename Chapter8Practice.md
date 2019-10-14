1
---

1-1) : 

/etc/services 는 디렉토리가 아니므로, 

~~~
$ grep tcp /etc/services 
~~~
> grep 명령어는<br>
> grep "패턴" 입력파일 임을 명시하자.

1-2) :

~~~
$ (grep tcp /etc/services | sort) > output.txt
~~~


2
---

2-1)

~~~
$ sort /etc/passwd > output.txt
~~~

2-2)

~~~
$ sort -r /etc/passwd > output.txt
~~~
> -r 은 reverse! 

2-3)

~~~
$ sort -t : -k 3 /etc/passwd > output.txt
~~~
> passwd 는 :로 필드를 구분하므로 필드 구분자로 :를 설정한다 <br>
> 옵션은 -t 라는 것을 꼭 기억하자 <br>
> 추가적으로 -k 옵션은 1번 행부터 시작한다

~~~
$ sort -t : +2 -3 /etc/passwd > output.txt
~~~
> 요 옵션은 k를 사용하지 않았을 때인데, <br>
> 이거는 이제 +n 부터 - (n-1) 까지의 필드를 정렬한다 <br>
> 요때는 이 필드번호가 0번부터 시작하니 주의하자.

2-4)

~~~
$ sort -n -t : -k 3 /etc/passwd > output.txt
~~~
> number ~~

or 

~~~
$ sort -n -t : -k +2 -3 /etc/passwd > output.txt
~~~

2-5)

~~~
$ sort -t : -k 5 /etc/passwd > output.txt
~~~

3
---

