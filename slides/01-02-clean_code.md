<!-- theme: default -->
<!-- paginate: true -->
<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->

# Clean Code

---

<!-- _footer: Martin: The Robert C. Martin Clean Code Collection, Pos. 815-922 -->

# What is Clean Code?

> * Can be read and enhanced by a developer other than its original
>   author
> * Has unit and acceptance tests
> * Does one thing well
> * Looks like it was written by someone who cares
> * Never obscures the designer‘s intent
> * Each routine you read turns out to be pretty much what you expected
> * Reads like well written prose
> * Provides a clear and minimal API
> * Elegant & efficient

---

# Names

---

# Intent

---

# Intent

```java
// ...
player1.setmenOCom(1);
player2.setmenOCom(0);
// ...
```

:bat: _Can you figure out what these functions are supposed to do?_

---

# The "Batman Mode" metaphor (:bat:)

When there is a mystery or crime to be solved, Batman will utilize his
brain and all kinds of fancy gadgets to get it done! He will analyze,
investigate and deduce until he has the answer. For him as a _costumed
Super Hero Detective_ it's part of the job! _Software engineers_ should
**never** have to go into Batman Mode to investigate about names used in
the code!

---

# Clarifying (:interrobang:) declaration

```java
public void setmenOCom(int a) {
  this.menOCom = a;
}
```

---

# Comment (:de:) to the rescue

```java
/**
 * setzt menOCom, 0 = Mensch, 1 = Computer
 *
 * @param int fuer menOCom
 */
public void setmenOCom(int a) {
  this.menOCom = a;
}
```

---

# Reveal your intent

```
import static PlayerType.*;
// ...
player1.setType(HUMAN);
player2.setType(COMPUTER);
// ...
```

```
public void setType(PlayerType type) {
  this.type = type;
}

public enum PlayerType {
  HUMAN, COMPUTER
}
```

---

# Reveal your intent (:bulb:)

* Any Variable/Method/Class name should tell
  * Why it exists
  * What it does
  * How it is used
* If you need a comment to explain the name, the name is probably ill
  chosen

---

# Meaning

---

# What might these services do? (:bat:)

```
Object - java.lang
|-AbstractService - de.logisticsworldwi.tools.impl
   |-AbstractSearchService - de.logisticsworldwi.shipment.impl
      |-LevelSearchService - de.logisticsworldwi.shipment.impl
        |-FirstLevelSearchService - de.logisticsworldwi.shipment.impl
        |-SecondLevelSearchService - de.logisticsworldwi.shipment.impl
          |-SecondLevelSearchBlackDeckerService - de.logisticsworldwi.shipment.impl
          |-SecondLevelSearchGlobalCustomerService - de.logisticsworldwi.shipment.impl
```

---

# Does the JavaDoc help? (:bat:)

```java
/**
 * level search service
 *
 * @author [censored]
/*
public class LevelSearchService {...}
```

---

# Maybe deeper down the class hierarchy? (:bat:)

```java
/**
 * This service provides methods for the Level-1 Shipment search.
 *
 * @author [censored]
/*
public class FirstLevelSearchService extends LevelSearchService {...}
```

```java
/**
 * This service provides methods for the Level-2 Shipment search.
 *
 * @author [censored]
/*
public class SecondLevelSearchService extends LevelSearchService {...}
```

---

# What `Level` means in this domain's language

* At the <https://logistics-worldwi.de> IT department the search for
  **publicly visible tracking information** of shipments is often called
  **First Level** Search
* The search for **more detailed (and sensitive) information** (which
  requires authentication) is often called **Second Level** Search

:information_source: _These are by no means official logistics terms!
They are not even used corporate-wide by <https://logistics-worldwi.de>
IT or business!_

---

# Say what you mean

```java
public class PublicTrackingShipmentSearchService extends ShipmentSearchService {}
public class FullVisibilityShipmentSearchService extends ShipmentSearchService {}
```

---

# Disinformation

---

:wrench: **TODO**

---

# Language

---

:wrench: **TODO**

---

# Encoding

---

:wrench: **TODO**

---

# Consistency

---

:wrench: **TODO**

---

# The Scope Rule

---

:wrench: **TODO**

---

# Functions

---

# Comments

---

# Formatting

