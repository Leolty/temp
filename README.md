# Factory Method Pattern and Abstract Factory Method Pattern

## Factory Method Pattern

The Factory Method pattern provides a way to create objects without specifying the exact class of the object that will be created. This is done by creating a method that returns a new instance of the required class, often by using an interface to define the method signature.

```java
// Common interface for all phones
interface Phone {
    void displayBrand();
}

class HuaweiPhone implements Phone {
    @Override
    public void displayBrand() {
        System.out.println("Huawei Phone");
    }
}

class IPhone implements Phone {
    @Override
    public void displayBrand() {
        System.out.println("Apple iPhone");
    }
}

class XiaomiPhone implements Phone {
    @Override
    public void displayBrand() {
        System.out.println("Xiaomi Phone");
    }
}

// Factory Method interface
interface PhoneFactory {
    Phone createPhone();
}

class HuaweiPhoneFactory implements PhoneFactory {
    @Override
    public Phone createPhone() {
        return new HuaweiPhone();
    }
}

class IPhoneFactory implements PhoneFactory {
    @Override
    public Phone createPhone() {
        return new IPhone();
    }
}

class XiaomiPhoneFactory implements PhoneFactory {
    @Override
    public Phone createPhone() {
        return new XiaomiPhone();
    }
}

public class FactoryMethodPatternDemo {
    public static void main(String[] args) {
        PhoneFactory huaweiPhoneFactory = new HuaweiPhoneFactory();
        PhoneFactory iPhoneFactory = new IPhoneFactory();
        PhoneFactory xiaomiPhoneFactory = new XiaomiPhoneFactory();

        Phone huaweiPhone = huaweiPhoneFactory.createPhone();
        Phone iPhone = iPhoneFactory.createPhone();
        Phone xiaomiPhone = xiaomiPhoneFactory.createPhone();

        huaweiPhone.displayBrand();
        iPhone.displayBrand();
        xiaomiPhone.displayBrand();
    }
}
```

## Abstract Factory Method Pattern

The Abstract Factory pattern provides an interface for creating related or dependent objects without specifying their concrete classes. Typically, it involves a series of factory methods, where each factory method is responsible for creating a different kind of object.

```java
// Common interfaces for Phones and Watches
interface Phone {
    void displayBrand();
}

interface Watch {
    void displayBrand();
}

// Concrete implementations for Phones
class HuaweiPhone implements Phone {
    @Override
    public void displayBrand() {
        System.out.println("Huawei Phone");
    }
}

class IPhone implements Phone {
    @Override
    public void displayBrand() {
        System.out.println("Apple iPhone");
    }
}

class XiaomiPhone implements Phone {
    @Override
    public void displayBrand() {
        System.out.println("Xiaomi Phone");
    }
}

// Concrete implementations for Watches
class HuaweiWatch implements Watch {
    @Override
    public void displayBrand() {
        System.out.println("Huawei Watch");
    }
}

class AppleWatch implements Watch {
    @Override
    public void displayBrand() {
        System.out.println("Apple Watch");
    }
}

class XiaomiWatch implements Watch {
    @Override
    public void displayBrand() {
        System.out.println("Xiaomi Watch");
    }
}

// Abstract Factory interface
interface DeviceFactory {
    Phone createPhone();
    Watch createWatch();
}

class HuaweiDeviceFactory implements DeviceFactory {
    @Override
    public Phone createPhone() {
        return new HuaweiPhone();
    }

    @Override
    public Watch createWatch() {
        return new HuaweiWatch();
    }
}

class AppleDeviceFactory implements DeviceFactory {
    @Override
    public Phone createPhone() {
        return new IPhone();
    }

    @Override
    public Watch createWatch() {
        return new AppleWatch();
    }
}

class XiaomiDeviceFactory implements DeviceFactory {
    @Override
    public Phone createPhone() {
        return new XiaomiPhone();
    }
    
    @Override
    public Watch createWatch() {
        return new XiaomiWatch();
    }
 }
 
public class AbstractFactoryPatternDemo {
    public static void main(String[] args) {
        DeviceFactory huaweiDeviceFactory = new HuaweiDeviceFactory();
        DeviceFactory appleDeviceFactory = new AppleDeviceFactory();
        DeviceFactory xiaomiDeviceFactory = new XiaomiDeviceFactory();
        
        Phone huaweiPhone = huaweiDeviceFactory.createPhone();
        Watch huaweiWatch = huaweiDeviceFactory.createWatch();
        Phone iPhone = appleDeviceFactory.createPhone();
        Watch appleWatch = appleDeviceFactory.createWatch();
        Phone xiaomiPhone = xiaomiDeviceFactory.createPhone();
        Watch xiaomiWatch = xiaomiDeviceFactory.createWatch();

        huaweiPhone.displayBrand();
        huaweiWatch.displayBrand();
        iPhone.displayBrand();
        appleWatch.displayBrand();
        xiaomiPhone.displayBrand();
        xiaomiWatch.displayBrand();
    }
}
```

## Key Differences between Factory Method and Abstract Factory Patterns:

1. Factory Method is a single-method factory that is responsible for creating a single type of object, whereas the Abstract Factory pattern involves a series of factory methods, with each method responsible for creating a different type of object.

2. Factory Method uses a single-method interface, whereas Abstract Factory uses a multi-method interface.

3. The Factory Method pattern is typically easier to implement and understand, as it involves only one type of object creation, while the Abstract Factory pattern can be more complex due to the creation of multiple types of objects.
