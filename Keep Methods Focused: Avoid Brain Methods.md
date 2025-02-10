<!-- #title -->
# Keep Methods Focused: Avoid Brain Methods

<!-- #severity -->
*Critical*

<!-- #categories -->
- maintainability
- readability

<!-- #description -->
## What is it?
This practice encourages breaking down complex methods that perform too many tasks (commonly known as "brain methods") into smaller, well-defined methods.

## Why apply it?
Highly complex methods are hard to read, test, and maintain. Splitting them into focused sub-methods improves clarity and modularity.

## How to Fix it?
Refactor large methods by extracting distinct functionalities into separate helper methods with clear responsibilities.

<!-- #examples -->

## Example 1: 
### Positive
<!-- This example breaks the order-processing method into several dedicated methods. -->
```java
public void processOrder(Order order) {
    validateOrder(order);
    calculateTotals(order);
    updateInventory(order);
    notifyCustomer(order);
}
```

### Negative
```java
public void processOrder(Order order) {
    // Validate order
    if (order == null || order.getItems().isEmpty()) {
        throw new IllegalArgumentException();
    }
    // Calculate totals
    double total = 0;
    for (Item item : order.getItems()) {
        total += item.getPrice() * item.getQuantity();
    }
    order.setTotal(total);
    // Update inventory
    for (Item item : order.getItems()) {
        Inventory.update(item);
    }
    // Notify customer
    EmailService.send(order.getCustomerEmail(), "Your order is processed");
    // Additional tasks mixed in...
}
```



