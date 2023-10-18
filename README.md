# JavaDesignPatterns
Exemplos de java design patterns

1. **Singleton Pattern (Padrão Singleton):**
   O Singleton garante que uma classe tenha apenas uma instância e fornece um ponto global de acesso a essa instância. Isso é útil quando você deseja uma única instância compartilhada em todo o sistema.

  java
   public class Singleton {
       private static Singleton instance;
       private Singleton() { }
       
       public static Singleton getInstance() {
           if (instance == null) {
               instance = new Singleton();
           }
           return instance;
       }
   }


2. **Factory Pattern (Padrão Factory):**
   O Factory Pattern é usado para criar objetos sem expor a lógica de criação diretamente ao cliente. Existem vários tipos de Factory Patterns, incluindo Factory Method e Abstract Factory.

   public interface Shape {
       void draw();
   }
   
   public class Circle implements Shape {
       public void draw() {
           System.out.println("Desenhar um círculo");
       }
   }
   
   public class Square implements Shape {
       public void draw() {
           System.out.println("Desenhar um quadrado");
       }
   }
   
   public class ShapeFactory {
       public Shape getShape(String shapeType) {
           if (shapeType.equalsIgnoreCase("CIRCLE")) {
               return new Circle();
           } else if (shapeType.equalsIgnoreCase("SQUARE")) {
               return new Square();
           }
           return null;
       }
   }
 

3. **Observer Pattern (Padrão Observer):**
   O Observer Pattern é usado para definir uma dependência um-para-muitos entre objetos. Quando o objeto observado muda de estado, todos os observadores são notificados e atualizados automaticamente.

   import java.util.ArrayList;
   import java.util.List;
   
   public interface Observer {
       void update(String message);
   }
   
   public class Subject {
       private List<Observer> observers = new ArrayList<>();
       
       public void attach(Observer observer) {
           observers.add(observer);
       }
       
       public void detach(Observer observer) {
           observers.remove(observer);
       }
       
       public void notifyObservers(String message) {
           for (Observer observer : observers) {
               observer.update(message);
           }
       }
   }


4. **Strategy Pattern (Padrão Strategy):**
   O Strategy Pattern é usado para definir uma família de algoritmos, encapsulá-los e torná-los intercambiáveis. Isso permite que o cliente escolha o algoritmo a ser usado em tempo de execução.


   public interface PaymentStrategy {
       void pay(int amount);
   }
   
   public class CreditCardPayment implements PaymentStrategy {
       public void pay(int amount) {
           System.out.println("Pagamento com cartão de crédito de R$" + amount);
       }
   }
   
   public class PayPalPayment implements PaymentStrategy {
       public void pay(int amount) {
           System.out.println("Pagamento com PayPal de R$" + amount);
       }
   }

