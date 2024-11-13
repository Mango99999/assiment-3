import java.util.ArrayList;

public class GroceryListApp {

    public static class GroceryItemOrder {
        private String name;
        private int quantity;
        private double pricePerUnit;

        public GroceryItemOrder(String name, double pricePerUnit) {
            this.name = name;
            this.pricePerUnit = pricePerUnit;
            this.quantity = 1;
        }

        public double getCost() {
            return quantity * pricePerUnit;
        }

        public void setQuantity(int quantity) {
            this.quantity = quantity;
        }

        public String getName() {
            return name;
        }

        public int getQuantity() {
            return quantity;
        }

        public double getPricePerUnit() {
            return pricePerUnit;
        }
    }

    public static class GroceryList {
        private ArrayList<GroceryItemOrder> items;
        private int size;

        public GroceryList() {
            items = new ArrayList<>();
            size = 0;
        }

        public void add(GroceryItemOrder item) {
            if (size < 10) {
                items.add(item);
                size++;
            } else {
                System.out.println("Cannot add more items. The list is full.");
            }
        }

        public double getTotalCost() {
            double totalCost = 0;
            for (GroceryItemOrder item : items) {
                totalCost += item.getCost();
            }
            return totalCost;
        }

        public void printList() {
            for (GroceryItemOrder item : items) {
                System.out.println(item.getName() + ": " + item.getQuantity() + " units, Total cost: " + item.getCost());
            }
        }
    }

    public static void main(String[] args) {
        GroceryList groceryList = new GroceryList();

        GroceryItemOrder item1 = new GroceryItemOrder("Cookies", 2.30);
        item1.setQuantity(4);

        GroceryItemOrder item2 = new GroceryItemOrder("Milk", 1.50);
        item2.setQuantity(2);

        GroceryItemOrder item3 = new GroceryItemOrder("Bread", 1.00);
        item3.setQuantity(3);

        groceryList.add(item1);
        groceryList.add(item2);
        groceryList.add(item3);

        System.out.println("Grocery List:");
        groceryList.printList();

        System.out.println("\nTotal Cost: " + groceryList.getTotalCost());
    }
}
