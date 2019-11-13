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
************************************************************************************************************************************
* Для дробных чисел double явялется дефолтным, поэтому

```java
float Num = 20.0; // ошибка incompatible types: possible lossy conversion from double to float в double приводится дефолтно, но написано float 
// НО
float Num = 20; // норм ,т.к преобр в integer, потому что float должен быть с F на конце
float Num = 20.0F;

```
************************************************************************************************************************************
* Системы счисления

* Основание  	Отличительный признак  	   Примеры	
* 2	           0b в начале числа	       0b00001111	
* 8	           0 в начале числа	01234343	
* 10	         нет	                      95459	
* 16	         0x в начале числа	  0x10ff

*  пример работы с 16 системой счисления
```java
class Main {
  public static void main(String[] args) {
  
    char a1 = '\u0F11';
    System.out.println(a1);// => ༑
  }
}

```
