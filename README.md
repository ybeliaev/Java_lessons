# Java_lessons
```java

class Main {
  public static void main(String[] args) {
    byte Num = 130;
    System.out.println(Num);
  }
}
/* error: incompatible types: possible lossy conversion from int to byte
    byte Num = 130;
               ^
1 error
compiler exit status 1
*/

*****************************************************
class Main {
  public static void main(String[] args) {
    byte Num = 10000000000000;

    System.out.println(Num);
  }
}
/*error: integer number too large
    byte Num = 10000000000000;
               ^
1 error
compiler exit status 1
Это потому что по-умолчанию числу присваиваетмя тип int, а значение больше возможного для этого типа
*/
// Так верно:
class Main {
  public static void main(String[] args) {
    long Num = 10000000000000L;

    System.out.println(Num);
  }
}
```
