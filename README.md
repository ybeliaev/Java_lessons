# Java_lessons
```java

public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
  public static void main(String[] args) {
  
    char a1 = '\u0F11';
    System.out.println(a1);// => ༑
  }
}

```
************************************************************************************************************************************
* Java Operators
```java
public class Main {
  public static void main(String[] args) {
  //форма записи присваивания
    int x = 1, y = 3;
    System.out.println(x);
    System.out.println(y);
  }
}
```
```java
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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
public class BankAccount {
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
* Название файла и класса в нём всегда одно и то же
* В пакете MyPack файл Main.java
```java
package MyPack
class Main {
  public static void main(String[] args) {  
    
    System.out.println(); 
    
  }
}
```
* Может быть только один public класс, но много других
```java
package MyPack
public class Main {
  public static void main(String[] args) {  
    
    System.out.println(); 
    
  }
  class Too {}
  class More {}
}
```
* Про точку входа. Она должна быть обязательно иначе код невыполним 
```java
package MyPack
public class Main {
  public static void main(String[] args) {      
    System.out.println();     
  }
 }
  class Too {
    public static void main(String[] args) {      
    System.out.println();     
    }
  }
  
// IDE вначале спросит какой класс исполнить, т.к есть ДВЕ точки входа main исполнив которую произойдёт выход
```
* Дефолтные значения типов данных (т.е сущность инициализированна, но значения не задано)
* byte, shot, int, long = 0
* float, double = 0.0
* char = 0 или '/u0000' где 0 - порядковый номер символа
* boolean = false
* Это было для примитивов. Для Reference это всегда ``` null ``` String туда же
***********************************************************************
* Instance variable
```java
class BankAccount {
  // id, name, balance - instance variable. Вызвать их в методе main как обычный примитив нельзя - они свойство класса
  int id;
  String name;
  double balance;
  public static void main(String[] args) {
    BankAccount MyAccount = new BankAccount(); 
    BankAccount YourAccount = new BankAccount();
    
    MyAccount.id = 1;
    MyAccount.name = "Jorgen";
    MyAccount.balance = 17.35;
    
    
    System.out.println(MyAccount.id); 
    
  }
}
```
******************************************
* Шаблон класса
```java
// class BankAccount в роли шаблона
public class BankAccount {
  int id;
  String name;
  double balance;
  
}
class MakeAccount {
  public static void main(String[] args) {
    BankAccount MyAccount = new BankAccount(); 
    BankAccount YourAccount = new BankAccount();
    
    MyAccount.id = 1;
    MyAccount.name = "Jorgen";
    MyAccount.balance = 17.35;    
    
    System.out.println(MyAccount.id); 
    
  }

}
```
*************************************************
* Дефолтные значения
```java
public class BankAccount {
  int id = 10;
  String name = "Аноним";
  double balance = 100;
  
}
class MakeAccount {
  public static void main(String[] args) {
    BankAccount MyAccount = new BankAccount(); 
    BankAccount YourAccount = new BankAccount();
    
    MyAccount.id = 1;
    MyAccount.name = "Jorgen";
    MyAccount.balance = 17.35;    
    
    System.out.println(MyAccount.id); 
    
  }

}
```
