# Detail of Objects

## If you declare a class by its parent class
```
public class Cat{
    final int color = 5;
    void miaomiao() {
        System.out.println("I am Cat");
    }

    final int getter() {
        return color;
    }
}

public class Persi extends Cat{
    void miaomiao() {
        System.out.println("I am Persi");
    }
    void name() {
        System.out.println("I am persi");
    }

    public static void main (String[] args) {
        Cat poly = new Persi();
        poly.miaomiao();
    }
}

// If you declare
persi Tom = new Persi();
pat Petter = new Persi();

tom.miaomiao() // "I am Persi"
petter.miaomiao() // "I am Persi"
//Conclusion: this is polymorphism

tom.name() // This is allowed
petter.name() //This is not allowed.
//Although, Petter is still Persi, but now you cannot use Persi's method.
//This is a little weird
System.out.println(tom.getClass()); // "Persi"
System.out.println(peter.getClass()); // "Persi" (Still Persi)

//Actually, even you use
Object Olive = new Persi();
System.out.println(Oliver.getClass()); // Still "Persi"

```

## If you change an object's type, something interesting happens

```
Cat tom = new Persi(); //Cat is a parent class
tom.name(); //This is NOT allowed
Persi peli= (Persi)tom;
peli.name(); //This is allowed, not doube!
tom.name();// This is ALLOWED! TOM has ability to use name()!
//This is understandable. Since the reference is just a remote control, tom also changed. 
//This happens secretly.
```
