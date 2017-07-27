## First Chapter

# DI with Java

---

#### Setter Injection

```java
public class Emailer {
    private SpellChecker spellChecker;
    public void setSpellChecker(SpellChecker spellChecker) {
        this.spellChecker = spellChecker;
    }
    ...
}
```

Here we create a setter method that can set spell checker for the Emailer. Through this setter method we attach Specific spell checker to our Emailer like below.

```java
Emailer service = new Emailer();
service.setSpellChecker(new FrenchSpellChecker());
```

```java
Emailer service = new Emailer();
service.setSpellChecker(new JapaneseSpellChecker());
```

#### ![](/assets/screenSetterInjection.png)

#### 

#### Constructor Injection

```java
public class Emailer {
    private SpellChecker spellChecker;
    public Emailer(SpellChecker spellChecker) {
        this.spellChecker = spellChecker;
    }
    ...
}
```

Here we create a constructor with spellCheker as input argument rather than no input arguments like below in order to achive flexibility of SpellChecker selection.

```java
public class Emailer {
    private SpellChecker spellChecker;
    public Emailer() {
        this.spellChecker = new SpellChecker();
    }
    ...
    public void send(String text) { .. }
}
```

By using constructor injection we have freedom to select whatever SpellChecker that we need with Emailer like below.

```java
Emailer service = new Emailer(new JapaneseSpellChecker());
```

And has following** advantages**:

* Being explicit about its contract - We can never create an Emailer without SpellChecker and forget about it's dependancies.



