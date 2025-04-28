# 🚛 Mega Java + Maven Assignment: **SmartSupplyChain**  - version 2
### Mastering Generics, OOP, Collections, Maven, and JUnit 5  
*Real-World Systems Engineering, the Modern Way*

---

## 🧠 Project Overview

You are tasked with building the core of **SmartSupplyChain**, a Java-powered logistics system that models the flow of products — from suppliers, through warehouses, to customers — **safely**, **scalably**, and **fault-tolerantly**.

Each module must follow:
- OOP (Encapsulation, Abstraction, Inheritance)
- Generics (Type Safety, Bounded Types, Wildcards)
- Exception Handling (Custom Exceptions, Validation)
- Collections (List, Map)
- Maven (Dependency Management)
- JUnit 5 (Professional Testing)
- System simulation (`main()` entrypoint)

---

# 🛠️ **Setup Instructions (MUST FOLLOW)**

✅ **Use IntelliJ IDEA**  
✅ **Use Maven to create the project**  
✅ **Use Java 17+**

---

# 1️⃣ Create a Maven Project in IntelliJ IDEA

**Steps:**

- Open IntelliJ IDEA → Click **New Project** → Choose **Maven**.
- Uncheck **Create from archetype** if it asks.
- Fill Project Details:

| Field | Value |
|:-----|:------|
| GroupId | `org.supplychain` |
| ArtifactId | `SmartSupplyChain` |
| Version | default (or `1.0-SNAPSHOT`) |

- Click **Finish**.

✅ Project structure will look like:

```
SmartSupplyChain/
 └── src/
     ├── main/
     │   └── java/
     └── test/
         └── java/
pom.xml
```

---

# 2️⃣ Fix the Maven Dependency

Maven may add an outdated JUnit 3.8 dependency! 🛑  
You **must replace it** with **JUnit 5**.

🔁 In `pom.xml`, replace:

```xml
<dependency>
  <groupId>junit</groupId>
  <artifactId>junit</artifactId>
  <version>3.8.1</version>
  <scope>test</scope>
</dependency>
```

with:

```xml
<dependency>
  <groupId>org.junit.jupiter</groupId>
  <artifactId>junit-jupiter-engine</artifactId>
  <version>5.9.1</version>
  <scope>test</scope>
</dependency>
```

✅ Now you can use **JUnit 5 annotations** like `@Test`, `@BeforeEach`, `@DisplayName`, etc.

---

# 3️⃣ **Project Structure**

Build this structure inside `src/main/java/`:

```
SmartSupplyChain/
 ├── main/
 │    └── SmartSupplyChainApp.java
 ├── items/
 │    ├── Product.java
 │    ├── Perishable.java
 │    ├── Document.java
 │    └── Electronic.java
 ├── inventory/
 │    ├── StorageUnit.java
 │    ├── MultiStorageUnit.java
 │    ├── Package.java
 │    └── Inventory.java
 ├── people/
 │    ├── Person.java
 │    ├── Supplier.java
 │    └── Customer.java
 ├── system/
 │    └── SupplyChainUtils.java
 └── exception/
      ├── ExpiredProductException.java
      ├── EmptyStorageException.java
      └── InvalidInputException.java
```

✅ Use appropriate Java Packages (`org.supplychain.items`, etc).

✅ Follow **best OOP practices**.

✅ Write **`SmartSupplyChainApp.java`** as the **simulation**.

---

# 4️⃣ **What to Implement (Tasks)**

---

## 🏗️ Task 1: Model Products

- Create `Product` (abstract) with `id`, `name`, and `abstract getType()`.
- Create concrete products:
  - `Document`
  - `Electronic`
  - `Perishable` (add `expirationDay`, `isExpired(today)` method).
- Expired products must throw `ExpiredProductException`.
- Use clean `toString()` overrides.

---

## 📦 Task 2: Generic Storage Units

- Create `StorageUnit<T>` for single items.
- Create `MultiStorageUnit<T>` for multiple items (`List<T>`).
- Handle null items and empty storage via custom exceptions.

---

## 🏢 Task 3: Packages and Inventory

- `Package<T>` groups multiple items.
- `Inventory<T>` maps package IDs to packages (`Map<String, Package<T>>`).
- Add methods to:
  - Add and retrieve packages
  - Validate contents
  - Handle expired products using exceptions

---

## 👨‍💼 Task 4: People (Supplier and Customer)

- `Person` (abstract) → common fields + methods.
- `Supplier` owns `List<Package<? extends Product>>`
- `Customer` can `receivePackage(Package<?>)`
- Handle invalid input with `InvalidInputException`.

---

## 🛠️ Task 5: Utility Methods

- Create `SupplyChainUtils`:
  - `displayItem(T item)`
  - `getExpired(List<? extends Perishable>, int today)`
  - `validateInput(String value)`

---

## 🧪 Task 6: Type Erasure Demo

- Create a `StorageUnit<Electronic>` and `StorageUnit<Document>`.
- Use reflection to show type erasure at runtime.
- Safely handle any exceptions.

---

## 🎮 Task 7: Simulation in SmartSupplyChainApp

- Create a full supply chain simulation in `main()`.
- Add suppliers, packages, inventory, customers.
- Catch and print all exceptions properly.
- Always finish with a `finally` block printing "System shutting down..."

---

# 5️⃣ **Testing Instructions (MUST-DO)**

✅ Create JUnit 5 Test classes under `src/test/java/` for:

| Class to Test | Test Class Name |
|:------------- |:--------------- |
| `Product` hierarchy | `ProductTest`, `PerishableTest`, etc. |
| `StorageUnit` | `StorageUnitTest` |
| `Package` and `Inventory` | `InventoryTest` |
| `Person`, `Supplier`, `Customer` | `PersonTest` |
| `SupplyChainUtils` | `SupplyChainUtilsTest` |

✅ Each test should:
- Test normal behavior (happy path).
- Test invalid behavior (exceptions).
- Use annotations:
  - `@Test`
  - `@BeforeEach`
  - `@AfterEach`
  - `@DisplayName`
  - `assertThrows()`
  - `assertEquals()`, `assertTrue()`, etc.

✅ Run all tests via:

```bash
mvn test
```
or inside IntelliJ IDEA (right-click → **Run 'All Tests'**)

✅ Green bar = success ✅

---

# 📬 Submission Requirements

✅ Full Maven project  
✅ Complete source code + simulation in `SmartSupplyChainApp`  
✅ Tests for **each major class**  
✅ GitHub repository named **SmartSupplyChain-YourName**  
✅ Updated `README.md` explaining:
- Project
- Structure
- Setup
- How to run tests
- Concepts covered

---

# 🧪 📚 **Expanded Testing Instructions for SmartSupplyChain**

---

# 1️⃣ **Where to Create Test Classes**

✅ Create all your tests under this folder:  
```
src/test/java/
```

✅ Maintain the **same package structure** as your `src/main/java` classes.

For example:

| Main Class Location | Test Class Location |
|:--------------------|:--------------------|
| `org.supplychain.items.Product` | `org.supplychain.items.ProductTest` |
| `org.supplychain.inventory.StorageUnit` | `org.supplychain.inventory.StorageUnitTest` |
| `org.supplychain.people.Supplier` | `org.supplychain.people.SupplierTest` |

✅ This keeps your project clean, organized, and **easy to navigate**.

---

# 2️⃣ **How to Write a Test Class**

Each Test Class should:

✅ Import JUnit 5 annotations:

```java
import org.junit.jupiter.api.*;

import static org.junit.jupiter.api.Assertions.*;
```

✅ Have this basic structure:

```java
class ClassNameTest {

    @BeforeEach
    void setUp() {
        // create new object before each test
    }

    @Test
    @DisplayName("Explain what this test does")
    void testSomething() {
        // arrange

        // act

        // assert
    }

    @AfterEach
    void tearDown() {
        // clean up if needed
    }
}
```

✅ Use **@DisplayName** to give your tests **human-readable names**.

---

# 3️⃣ **What to Test**

✅ **Test positive behavior** ("Happy Path"):

| Example |
|:--------|
| Adding a product successfully |
| Storing and retrieving from StorageUnit |
| Receiving a valid package as Customer |

---

✅ **Test negative behavior** ("Sad Path" or Exception Handling):

| Example |
|:--------|
| Trying to add a null product throws `InvalidInputException` |
| Retrieving from an empty StorageUnit throws `EmptyStorageException` |
| Receiving expired items throws `ExpiredProductException` |
| Creating a Person with blank name throws `InvalidInputException` |

---

✅ **Test edge cases**:

| Example |
|:--------|
| Adding the same product twice |
| Storing a package with 0 items |
| Handling a large number of items |

---

# 4️⃣ **Best Practices When Writing Tests**

✅ **Isolate Each Test**  
- Each test must **work independently**.
- Use `@BeforeEach` to **setup a fresh environment**.

✅ **Write Small Tests**  
- Focus each test on **one thing only**.
- If a test fails, it should be **obvious why**.

✅ **Use the Right Assertions**

| Assertion | Use it for |
|:----------|:-----------|
| `assertEquals(expected, actual)` | Comparing values |
| `assertTrue(condition)` | Checking a boolean condition |
| `assertFalse(condition)` | Checking something is false |
| `assertThrows(Exception.class, () -> {...})` | Checking that an exception is thrown |
| `assertAll(...)` | Running multiple assertions together |

✅ **Readable Naming**

- Method names should explain what you are testing, e.g.,

```java
void shouldAddProductSuccessfully()
void shouldThrowWhenAddingNullProduct()
```

✅ **Group Related Assertions Together**

If you need multiple checks for one object, use `assertAll()`:

```java
assertAll(
    () -> assertEquals("Milk", product.getName()),
    () -> assertEquals(3.5, product.getPrice(), 0.01),
    () -> assertEquals("Perishable", product.getType())
);
```

---

# 5️⃣ **How to Run Your Tests**

✅ You have **two ways**:

### Method 1: Inside IntelliJ IDEA
- Right-click on the test class (e.g., `ProductTest`) → **Run 'ProductTest'**
- Or right-click on `src/test/java` → **Run all tests**

✅ Look for a **Green Bar** = All tests passed.

---

### Method 2: Using Maven Command Line

Open the terminal in your project root and run:

```bash
mvn clean test
```

✅ Maven will build the project and run all tests.
✅ You will see detailed test results in the console.

---

# 6️⃣ **Common Mistakes to Avoid**

| Mistake | Fix |
|:--------|:----|
| Forgetting to replace JUnit 3 with JUnit 5 | Make sure your `pom.xml` uses JUnit 5 dependency |
| Writing multiple things in one test | Focus on one scenario per test |
| Forgetting `@Test` annotation | No `@Test` = method will not run as a test |
| Modifying shared state between tests | Use `@BeforeEach` to reset everything |
| Missing exception handling tests | Always test invalid inputs and error cases |
| Hardcoding lots of values without using constants | Try to keep test data consistent and clean |

---

# 7️⃣ **Example: StorageUnitTest**

Here’s a **full example** of a properly written test class for `StorageUnit<T>`:

```java
package org.supplychain.inventory;

import org.junit.jupiter.api.*;
import org.supplychain.exception.EmptyStorageException;
import org.supplychain.exception.InvalidInputException;
import org.supplychain.items.Document;

import static org.junit.jupiter.api.Assertions.*;

class StorageUnitTest {

    private StorageUnit<Document> storageUnit;

    @BeforeEach
    void setUp() {
        storageUnit = new StorageUnit<>();
    }

    @Test
    @DisplayName("Should add and retrieve item successfully")
    void testAddAndGetItem() throws EmptyStorageException, InvalidInputException {
        Document document = new Document("D001", "Shipping Manifest");
        storageUnit.addItem(document);

        assertEquals(document, storageUnit.getItem());
    }

    @Test
    @DisplayName("Should throw when adding null item")
    void testAddNullItem() {
        assertThrows(InvalidInputException.class, () -> {
            storageUnit.addItem(null);
        });
    }

    @Test
    @DisplayName("Should throw when getting from empty storage")
    void testGetFromEmptyStorage() {
        assertThrows(EmptyStorageException.class, () -> {
            storageUnit.getItem();
        });
    }
}
```

✅ Notice:
- Clean readable structure
- Good method names
- Testing both normal and error cases
- Using proper assertions

---

# ✅ Minimum Testing Checklist for Submission

| Test Class | Coverage Needed |
|:-----------|:----------------|
| ProductTest | Test `id`, `name`, `type` |
| PerishableTest | Test expiration logic |
| StorageUnitTest | Test adding and retrieving items |
| PackageTest | Test adding items, retrieving items |
| InventoryTest | Test mapping and retrieving packages |
| SupplierTest | Test adding and providing packages |
| CustomerTest | Test receiving packages and handling expired |
| SupplyChainUtilsTest | Test display, validation, expiration detection |

---

# 🎯 Bonus Tip

If you want to impress your instructor even more:  
✅ Add a **Test Suite** that groups all tests to run together  
✅ Use `@Nested` classes inside test classes to group similar tests.

---

# 😄 Final Pep Talk on Testing

> "Tests are not just to catch bugs —  
> they're like your loyal army defending your castle!  
> No stronghold ever survived with weak defenses.  
> Be the developer who always tests."

---

---

# 📈 Grading Rubric (Suggested)

| Item | Points |
|:-----|:-------|
| Correct Maven setup | 10 |
| Code structure & OOP design | 20 |
| Proper exception handling | 20 |
| Usage of Generics | 20 |
| Complete simulation and flow | 20 |
| Full unit test coverage | 20 |
| GitHub + README.md | 10 |
| **Total** | **100 points** |

---

# 🎯 Extra Challenges (Optional)

- Create CLI interaction via `Scanner`.
- Use Java Logger instead of `System.out`.
- Build retry logic after exceptions.
- Add timestamps to logs.

---

# 😄 Motivational Closing

> "Good supply chains deliver goods.  
> Great supply chains deliver goods **safely, on time, and with clean tested code**!  
> Be a professional — not a PHP cargo cultist! 🚛✨"

