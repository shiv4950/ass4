*************************************componentclass.java******************
#componentclass.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q1;

interface Component {
   void showDetails();
}
#fileclass.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q1;

class File implements Component {
   private String name;

   public File(String name) {
      this.name = name;
   }

   public void showDetails() {
      System.out.println("File: " + this.name);
   }
}

#folderclass.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q1;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

class Folder implements Component {
   private String name;
   private List<Component> components = new ArrayList();

   public Folder(String name) {
      this.name = name;
   }

   public void addComponent(Component component) {
      this.components.add(component);
   }

   public void removeComponent(Component component) {
      this.components.remove(component);
   }

   public void showDetails() {
      System.out.println("Folder: " + this.name);
      Iterator var2 = this.components.iterator();

      while(var2.hasNext()) {
         Component component = (Component)var2.next();
         component.showDetails();
      }

   }
}
#main.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q1;

public class Main {
   public Main() {
   }

   public static void main(String[] args) {
      File file1 = new File("Document1.txt");
      File file2 = new File("Photo.jpg");
      File file3 = new File("Music.mp3");
      Folder rootFolder = new Folder("Root");
      Folder documentsFolder = new Folder("Documents");
      Folder mediaFolder = new Folder("Media");
      documentsFolder.addComponent(file1);
      mediaFolder.addComponent(file2);
      mediaFolder.addComponent(file3);
      rootFolder.addComponent(documentsFolder);
      rootFolder.addComponent(mediaFolder);
      rootFolder.showDetails();
   }
}
***************************************************vehicale&*****************************************
#carclass.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q2;

class Car extends Vehicle {
   public Car(Engine engine) {
      super(engine);
   }

   public void startEngine() {
      System.out.print("Car: ");
      this.engine.startEngine();
   }

   public void stopEngine() {
      System.out.print("Car: ");
      this.engine.stopEngine();
   }
}

#electicengineclass.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q2;

class ElectricEngine implements Engine {
   ElectricEngine() {
   }

   public void startEngine() {
      System.out.println("Starting electric engine...");
   }

   public void stopEngine() {
      System.out.println("Stopping electric engine...");
   }
}

#engine.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q2;

interface Engine {
   void startEngine();

   void stopEngine();
}

#motorbike.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q2;

abstract class Vehicle {
   protected Engine engine;

   public Vehicle(Engine engine) {
      this.engine = engine;
   }

   abstract void startEngine();

   abstract void stopEngine();
}


#main.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q2;

public class Main {
   public Main() {
   }

   public static void main(String[] args) {
      Vehicle petrolCar = new Car(new PetrolEngine());
      petrolCar.startEngine();
      petrolCar.stopEngine();
      Vehicle electricCar = new Car(new ElectricEngine());
      electricCar.startEngine();
      electricCar.stopEngine();
      Vehicle petrolBike = new Motorbike(new PetrolEngine());
      petrolBike.startEngine();
      petrolBike.stopEngine();
      Vehicle electricBike = new Motorbike(new ElectricEngine());
      electricBike.startEngine();
      electricBike.stopEngine();
   }
}
#vehicle.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q2;

abstract class Vehicle {
   protected Engine engine;

   public Vehicle(Engine engine) {
      this.engine = engine;
   }

   abstract void startEngine();

   abstract void stopEngine();
}
********************************************************employee manager*****************************************************

#employee.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q3;

class Employee implements EmployeeComponent {
   private String name;
   private String position;

   public Employee(String name, String position) {
      this.name = name;
      this.position = position;
   }

   public void showDetails() {
      System.out.println(this.position + ": " + this.name);
   }

   public void add(EmployeeComponent employee) {
      throw new UnsupportedOperationException("Employees cannot add subordinates.");
   }

   public void remove(EmployeeComponent employee) {
      throw new UnsupportedOperationException("Employees cannot remove subordinates.");
   }
}

#employeecomponent.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q3;

interface EmployeeComponent {
   void showDetails();

   void add(EmployeeComponent var1);

   void remove(EmployeeComponent var1);
}

#main.java// Source code is decompiled from a .class file using FernFlower decompiler.
package Q3;

public class Main {
   public Main() {
   }

   public static void main(String[] args) {
      Employee emp1 = new Employee("Alice", "Developer");
      Employee emp2 = new Employee("Bob", "Designer");
      Employee emp3 = new Employee("Charlie", "Tester");
      Manager manager1 = new Manager("David", "Project Manager");
      manager1.add(emp1);
      manager1.add(emp2);
      Manager manager2 = new Manager("Eve", "QA Manager");
      manager2.add(emp3);
      Manager generalManager = new Manager("Frank", "General Manager");
      generalManager.add(manager1);
      generalManager.add(manager2);
      generalManager.showDetails();
   }
}


#manager.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q3;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

class Manager implements EmployeeComponent {
   private String name;
   private String position;
   private List<EmployeeComponent> subordinates = new ArrayList();

   public Manager(String name, String position) {
      this.name = name;
      this.position = position;
   }

   public void showDetails() {
      System.out.println(this.position + ": " + this.name);
      Iterator var2 = this.subordinates.iterator();

      while(var2.hasNext()) {
         EmployeeComponent subordinate = (EmployeeComponent)var2.next();
         subordinate.showDetails();
      }

   }

   public void add(EmployeeComponent employee) {
      this.subordinates.add(employee);
   }

   public void remove(EmployeeComponent employee) {
      this.subordinates.remove(employee);
   }
}
***************************************************************bankAcountclass**************************************************
#bankaccount.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q4;

interface BankAccount {
   void deposit(double var1);

   void withdraw(double var1);

   double getBalance();
}

#bankaccountproxy.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q4;

class BankAccountProxy implements BankAccount {
   private RealBankAccount realBankAccount;

   public BankAccountProxy(double initialBalance) {
      this.realBankAccount = new RealBankAccount(initialBalance);
   }

   public void deposit(double amount) {
      this.realBankAccount.deposit(amount);
   }

   public void withdraw(double amount) {
      if (this.realBankAccount.getBalance() >= amount) {
         this.realBankAccount.withdraw(amount);
      } else {
         System.out.println("Insufficient balance. Withdrawal denied.");
      }

   }

   public double getBalance() {
      return this.realBankAccount.getBalance();
   }
}

#main.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q4;

public class Main {
   public Main() {
   }

   public static void main(String[] args) {
      BankAccount account = new BankAccountProxy(100.0);
      account.deposit(50.0);
      System.out.println("Current Balance: " + account.getBalance());
      account.withdraw(80.0);
      System.out.println("Current Balance: " + account.getBalance());
      account.withdraw(100.0);
      System.out.println("Current Balance: " + account.getBalance());
   }
}
#realbankaccount.java
// Source code is decompiled from a .class file using FernFlower decompiler.
package Q4;

class RealBankAccount implements BankAccount {
   private double balance;

   public RealBankAccount(double initialBalance) {
      this.balance = initialBalance;
   }

   public void deposit(double amount) {
      this.balance += amount;
      System.out.println("Deposited: " + amount);
   }

   public void withdraw(double amount) {
      this.balance -= amount;
      System.out.println("Withdrew: " + amount);
   }

   public double getBalance() {
      return this.balance;
   }
}
