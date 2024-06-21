# 13.06.2024-Java-individual-work

## Main.java

import java.util.Scanner;
public class Main {
    private static Scanner scanner = new Scanner(System.in);
    private static CheeseShop cheeseShop = new CheeseShop();
  
    public static void main(String[] args) {
      
        while(true){
            System.out.println("Press 1, to add a cheese");
            System.out.println("Press 2, to print all cheese types");
            System.out.println("Press 3, to remove a cheese");
            System.out.println("Press 4, to see updated cheese list");
            System.out.println("Press 5, to exit");
            int action = scanner.nextInt();
           
            if (action == 1){
                addCheese();
            } else if (action == 2){
                printCheeses();
            } else if (action == 3){
                removeCheese();
            } else if (action == 4){
                updateCheese();
            } else{
                break;
            }
        }

    }

    public static void addCheese(){
        System.out.println("Provide an cheese batch number"); 
        int batchNumber = scanner.nextInt();
        System.out.println("Provide an cheese name");
        String cheeseName = scanner.next();
        System.out.println("Provide an cheese price");
        int price = scanner.nextInt();
      
        Cheese cheese = new Cheese(batchNumber, cheeseName, price);
        CheeseShop.addCheese(cheese);
    }

    public static void printCheeses(){
        System.out.println("These are cheeses in the storage");
        for (Cheese cheese : CheeseShop.getCheeses()){
            System.out.println(cheese.getBatchNumber() + cheese.getCheeseName() + cheese.getPrice());
        }
    }
    public static void removeCheese(){
        System.out.println("Provide the cheese batch number to remove it from list");
        int batchNumber = scanner.nextInt();
        if (cheeseService.removeCheese(batchNumber)) {
              System.out.println("Cheese removed from the list.");
        } else {
              System.out.println("Cheese not found.");
          }
      }

    public static void updateCheese(){
        System.out.println("Provide the cheese batch number to update the list");
        int batchNumber = scanner.nextInt();
        System.out.println("Provide the new Cheese name");
        String CheeseName = scanner.next();
        System.out.println("Provide the new cheese price");
        int price = scanner.nextInt();
        CheeseService.updateCheese(batchNumber, CheeseName, price);
        System.out.println("Cheese updated successfully");
    }

}


## Cheese.java

public class Cheese {
  private int batchNumber;
  private String CheeseName;
  private int price;

  public Cheese(int batchNumber, String CheeseName, int price) {
    this.batchNumber = batchNumber;
    this.CheeseName = CheeseName;
    this.price = price;
  }

  public int getBatchNumber() {
    return batchNumber;
  }

  public String getCheeseName() {
    return CheeseName;
  }

  public void setCheeseName(String cheeseName) {
    this.CheeseName = CheeseName;
  }

  public int getPrice() {
    return price;
  }

  public void setPrice(int price) {
    this.price = price;
  }
}

## CheeseShop.java 

import java.util.ArrayList; 

public class CheeseShop{

private ArrayList<Cheese> cart = new ArrayList<Cheese>();

  public void addCheeseToCart(Cheese cheese) {
   
    cart.add(cheese);
  }

  public int checkout(){ 
  int sum = 0; 
  for(var cheese : cart){
    sum += cheese.getPrice(); 
  }
 return sum;  
  }     
}

## CheeseService.java 

import java.util.ArrayList; 
public class CheeseService{

   private ArrayList<Cheese>cheeses = new ArrayList<Cheese>();

   public ArrayList<Cheese> getCheeses(){
    return cheeses; 
  }

  public void addCheese(Cheese cheese){ 
   cheeses.add(cheese);
  } 

  public void removeCheese(int batchNumber){ 
   for (var cheese : cheeses){ 
     
     if (cheese.getBatchNumber() == batchNumber){ 
       cheeses.remove(cheese);
       return; 
       }
      }
     }
  public void updateCheese(int batchNumber, String CheeseName, int price){ 
  for (var cheese : cheeses){ 
     if (cheese.getBatchNumber() == batchNumber){ 
       cheese.setCheeseName(CheeseName);
       cheese.setPrice(price);
       return; 
      }
    }
  }
}
