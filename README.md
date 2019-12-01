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
************************************************************************************************************************************
* Java Operators
```java
class Main {
  public static void main(String[] args) {
  //форма записи присваивания
    int x = 1, y = 3;
    System.out.println(x);
    System.out.println(y);
  }
}
```
```java
class Main {
  public static void main(String[] args) {
  
    int x = 1, y = 3;
    System.out.println(x/y);// 0

    double a = 11, b = 3;
    System.out.println(a/b); // 3.6666666666666665

    
    int z = 1, c = 2;
    int v = z + ++c;
    System.out.println(v); // 4
    System.out.println(c); // 3
  }
}
```
```java
class Main {
  public static void main(String[] args) {
  
    long x = 1000L;
    int y  = x;
    System.out.println(y);// error: incompatible types: possible lossy conversion from long to int
  // но если
  
  short z = 1000;
  int c = z;
  System.out.println(c); // 1000, т.к int -> short
    
  }
}
```
* Bitwise operators
```java
class Main {
  public static void main(String[] args) {
  
    int x = 10;
    int y = 20;
    boolean c = x!=y || ++y > x;
    // операция НЕ дойдёт до правой части сравнения
    // НО если bitwise operators ( | или & )то исполнится вся строка и y будет равен 21
    System.out.println(y); // y равен 20
    System.out.println(c);
  }
}
```
* System.out.println(10 & 6); результат = 2
* 1010 10 в 2 системе
* 0110 6 в 2 системе
* -----
* 0010 это 2 
* System.out.println(10 & 6); результат = 1110это 14
******************************************************
* XOR
```java
class Main {
  public static void main(String[] args) {
  
    boolean a1 = true;
    boolean a2 = false;
    boolean a3 = false;
    System.out.println(a1^a2^a3); // true т.к ОДИН операнд true
    
  }
}
```
**************************************************
* операции с ``` char ```
```java
char x = 'a';
 int y = 10;
    System.out.println(x + y); // будет 97 + 10 = 107
```
**************************************************
* Создание класса
Класс - reference data type (ссылочный тип данных)
```java
class BankAccount {
  int id;
  String name;
  double balance;
  public static void main(String[] args) {
    BankAccount MyAccount = new BankAccount(); // BankAccount есть типом данных для переменной MyAccount
    // new BankAccount() - вызов конструктора, создание нового объекта
    BankAccount YourAccount = new BankAccount();
    
    MyAccount.id = 1;
    MyAccount.name = "Jorgen";
    MyAccount.balance = 17.35;
    
    
    System.out.println(MyAccount.id); 
    
  }
}
```
