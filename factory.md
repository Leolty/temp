## implement the Factory Method Pattern

### Step 1: define a common interface for all phones:

```java
public interface Phone {
    void display();
}
```

### step 2: create specific phone classes that implement the `Phone` interface:

```java
public class HuaweiPhone implements Phone {
    @Override
    public void display() {
        System.out.println("This is a Huawei phone");
    }
}

public class IPhone implements Phone {
    @Override
    public void display() {
        System.out.println("This is an iPhone");
    }
}

public class XiaomiPhone implements Phone {
    @Override
    public void display() {
        System.out.println("This is a Xiaomi phone");
    }
}
```

### Step 3: Create a `PhoneFactory` interface with a `createPhone` method:

```java
public interface PhoneFactory {
    Phone createPhone();
}
```

### step 4: Create specific factory classes for each phone that implement the `PhoneFactory` interface:
```java
public class HuaweiPhoneFactory implements PhoneFactory {
    @Override
    public Phone createPhone() {
        return new HuaweiPhone();
    }
}

public class IPhoneFactory implements PhoneFactory {
    @Override
    public Phone createPhone() {
        return new IPhone();
    }
}

public class XiaomiPhoneFactory implements PhoneFactory {
    @Override
    public Phone createPhone() {
        return new XiaomiPhone();
    }
}
```

### Step 5: Use the factory method pattern to create instances of different phone types:
```java
public class Main {
    public static void main(String[] args) {
        PhoneFactory huaweiFactory = new HuaweiPhoneFactory();
        PhoneFactory iPhoneFactory = new IPhoneFactory();
        PhoneFactory xiaomiFactory = new XiaomiPhoneFactory();

        Phone huaweiPhone = huaweiFactory.createPhone();
        Phone iPhone = iPhoneFactory.createPhone();
        Phone xiaomiPhone = xiaomiFactory.createPhone();

        huaweiPhone.display();
        iPhone.display();
        xiaomiPhone.display();
    }
}
```

### Expected Output:

```
This is a Huawei phone
This is an iPhone
This is a Xiaomi phone
```
