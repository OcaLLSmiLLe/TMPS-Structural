# Structural Design Patterns
# Author: Grecu Octavian
# Group: FAF 191
## Table of Contents
- [Adapter](#adapter)
- [Composite](#composite)
- [Decortor](#decorator)
- [Facade](#facade)

## Adapter <a name="adapter"></a>
- Bridge between 2 interfaces (Useful when we work with Legacy code)
# Adapter code sample
...
public class AdapterExample {

    public static void main(String[] args) {

        AndroidCharger androidCharger = new AndroidCharger();
        AndroidPhone androidPhone = new OnePlus5();
        androidCharger.charge(androidPhone);

        IPhoneCharger iPhoneCharger = new IPhoneCharger();
        IPhone iPhone = new IPhoneX();
        iPhoneCharger.charge(iPhone);

        AndroidToIPhoneAdapter adapter = new AndroidToIPhoneAdapter(androidPhone);
        iPhoneCharger.charge(adapter);


    }
}

...
### Disadvantages
- No new functionalities
- Multiple Adapters

## Composite <a name="composite"></a>
- Tree structure
- Component
- Leaf
- Composite
# Composite code sample
...
public class CompositeExample {

    public static void main(String[] args) {

        Employee developer1 = new Developer("Peter", 1, 100L);
        Employee developer2 = new Developer("Sam", 2, 200L);
        Employee developer3 = new Developer("Ryan", 3, 200L);
        Employee developer4 = new Developer("Ryan V", 6, 200L);
        Employee developer5 = new Developer("Ryan X", 7, 200L);
        Employee lead1 = new Lead("Mike", 4, 2000L);
        Employee lead2 = new Lead("Chris", 5, 2000L);
        Employee manager = new Manager("Will", 8, 50000L);



        lead1.add(developer1);
        lead1.add(developer2);
        lead1.add(developer3);

        System.out.println(lead1.toString());
        lead2.add(developer4);
        System.out.println(lead2.toString());

        manager.add(lead1);
        manager.add(lead2);
        manager.add(developer5);


        System.out.println(manager.toString());


    }
}

...
### Disadvantages
- Very costly to create more composite impl
- Overly simple

## Decorator <a name="decorator"></a>
- Wrapper
- Add functionality or behavior
- Single Responsibility Principle
- Dynamically compose behavior
- Inheritance and Composition
# Decorator code sample
...
public class DecoratorExample {

    public static void main(String[] args) {


        Phone androidPhone = new AndroidPhone(new BasicPhone());
        System.out.println(androidPhone.build());


        Phone applePhone = new ApplePhone(new BasicPhone());
        System.out.println(applePhone.build());


        Phone nokiaWindowsPhone = new NokiaPhone(new WindowsPhone(new BasicPhone()));
        System.out.println(nokiaWindowsPhone.build());

        Phone nokiaAndroidPhone = new NokiaPhone(new AndroidPhone(new BasicPhone()));
        System.out.println(nokiaAndroidPhone.build());

    }
}

...
## Disadvantages
- New Class for every feature
- no of objects (more)
- more comples for the clients

## Facade <a name="facade"></a>
- Make API easy 
- Interface not required
- usually a refactoring pattern
# Facade code sample
...
public class FacadeDemo {

    public static void main(String[] args) {

        FacadePhone facadePhone = new FacadePhone();

        System.out.println(facadePhone.buildAndroidPhone());
        System.out.println(facadePhone.buildApplePhone());
        System.out.println(facadePhone.buildMicrosoftPhone());

    }
}



...
## Disadvantages
- Over usage
- Clean up design pattern