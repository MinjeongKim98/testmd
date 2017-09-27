Combintaion (factorial vs recursive)
===
초기 코드
-----
##factorial combination

*recursive factorial을 이용하여 m!, n! (m-n)!의 값을 구해 combination의 값을 구하였다.
*int 형으로 숫자를 받는다는 가정 하에 코드를 작성했기에 int형이 아닌 다른 type의 변수가 들어왔을 때의 error처리는 별도로 하지 않았다.

##recursive factorial

*factorial을 이용하지 않고 combination함수 내의 조건을 만족할 때까지 수를 줄여가며 함수를 반복적으로 실행하였다.
*int형으로 숫자를 입력 받는다는 가정 하에 코드를 작성했기에 int형이 아닌 다른 type의 변수가 들어왔을 때의 error처리는 하지 않았지만, m과 n이 0이 되었을 때 실행 해야 할 조건은 작성하였다.

------------
Code Review 후
----------
<factorial combination>

*초반에는 n!, m! 등의 각 결과 값을 다른 변수에 저장한 후 return 하도록 작성하였으나 변수가 여러개이면 다른 개발자가 이 코드를 보았을 때 헷갈려 할 것이라는 조언이 있어 수정하였다.
|||x = n-m
+        result = factorial(n)/(factorial(n-m) * factorial(m))
-        n = factorial(n)
-        m = factorial(m)
-        x = factorial(x)
-        result = n/(x*m)
         return result|||
위와 같았던 코드를
|||result = factorial(n)/(factorial(n-m) * factorial(m))
   return = result|||
로 수정하였다.

*초반 코드에서는 x = m-n이라는 변수도 존재햤었는데, 이는 n과 m의 factorial을 계산한 후 (n-m)!을 계산하면 의도한 숫자와 다른 결과값이 나오기 때문에 초기에 x라는 변수를 입력했었다. 하지만 이는 순서를 바꿈으로써 해결되었고, 그 후 수정이 더해져 위와 같은 코드가 되었다.

*combination을 하는 이유가 경우의 수를 계산하는 것이기 때문에 실제 존재하지 않는 결과값은 본래 입력한 string이 아닌 경우의 수가 존재하지 않는 다는 의미로 return 0을 해주는 것이 더 명확하고 좋은 코드가 될 것이라는 조언을 받아
'''else:
       print("cannot be calculated)'''
라는 본래 코드를
'''else:
       return 0'''
으로 수정하였다.

##recursive combination

*int형으로 문자를 받기 때문에
'''elif int(num) < 0:'''
이러한 코드에서 num을 int형으로 강제 형변환을 할 필요가 없어졌으므로
'''elif num < 0:'''
으로 변경하여 쓸모없는 작업을 삭제하였다.

*2학기 초기에 정했던 rule에 따라
'''if n>m'''
코드를
'''if n > m'''
으로 변경하였다.

-------------------
