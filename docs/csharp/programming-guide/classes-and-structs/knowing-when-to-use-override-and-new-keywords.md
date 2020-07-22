---
title: Geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme-C# Programlama Kılavuzu
description: Temel ve türetilmiş sınıfta aynı ada sahip yöntemlerin nasıl etkileşime gireceğini belirtmek Için C# ' deki New ve override anahtar sözcüklerini kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 732a37c08b4c7bb998a7cc5dcfbd00d4e706b06c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864546"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)

C# ' de, türetilmiş sınıftaki bir yöntem, temel sınıftaki bir yöntemle aynı ada sahip olabilir. Yöntemlerinin [New](../../language-reference/keywords/new-modifier.md) ve [override](../../language-reference/keywords/override.md) anahtar sözcüklerini kullanarak nasıl etkileşime gireceğini belirtebilirsiniz. `override`Değiştirici, *extends* temel sınıf yöntemini genişletir `virtual` ve `new` değiştirici, erişilebilir bir temel sınıf yöntemini *gizler* . Fark, bu konudaki örneklerde gösterilmiştir.  
  
 Konsol uygulamasında, aşağıdaki iki sınıfı bildirin `BaseClass` ve `DerivedClass` . `DerivedClass`öğesinden devralır `BaseClass` .  
  
```csharp  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
```  
  
 Yönteminde, `Main` ve değişkenlerini bildirin `bc` `dc` `bcdc` .  
  
- `bc`türündedir `BaseClass` ve değeri türündedir `BaseClass` .  
  
- `dc`türündedir `DerivedClass` ve değeri türündedir `DerivedClass` .  
  
- `bcdc`türündedir `BaseClass` ve değeri türündedir `DerivedClass` . Bu, dikkat edilmesi gereken değişkendir.  
  
 `bc`Ve `bcdc` türü olduğundan `BaseClass` , atama kullanmadığınız müddetçe yalnızca doğrudan erişim sağlayabilir `Method1` . Değişken, `dc` `Method1` ve ' a erişebilir `Method2` . Bu ilişkiler aşağıdaki kodda gösterilmiştir.  
  
```csharp  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
```  
  
 Ardından, aşağıdaki `Method2` yöntemi öğesine ekleyin `BaseClass` . Bu yöntemin imzası `Method2` içindeki yönteminin imzasıyla eşleşir `DerivedClass` .  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 `BaseClass`Artık bir yöntemi olduğundan `Method2` , `BaseClass` `bc` `bcdc` aşağıdaki kodda gösterildiği gibi, değişkenler için ikinci bir çağırma açıklaması eklenebilir.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Projeyi derlediğinizde, `Method2` içinde yönteminin eklenmesi `BaseClass` bir uyarıya neden olur. Uyarı, `Method2` içindeki yönteminin `DerivedClass` içindeki yöntemi gizlediğini belirtir `Method2` `BaseClass` . `new`Bu sonuca neden olmak istiyorsanız, tanımda anahtar sözcüğünü kullanmanız önerilir `Method2` . Alternatif olarak, `Method2` uyarıyı çözümlemek için yöntemlerden birini yeniden adlandırabilirsiniz, ancak her zaman pratik değildir.  
  
 Eklemeden önce `new` , ek çağırma deyimleri tarafından üretilen çıktıyı görmek için programı çalıştırın. Aşağıdaki sonuçlar görüntülenir.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new`Anahtar sözcüğü, bu çıktıyı üreten ilişkileri korur, ancak uyarıyı bastırır. Türüne sahip değişkenler `BaseClass` , üyelerine erişmeye devam `BaseClass` eder ve türüne sahip olan değişken `DerivedClass` ilk olarak üyelere erişmeye devam eder `DerivedClass` ve öğesinden devralınan üyeleri göz önünde bulundurun `BaseClass` .  
  
 Uyarıyı bastırmak için, `new` `Method2` `DerivedClass` aşağıdaki kodda gösterildiği gibi değiştiricisini içindeki tanımına ekleyin. Değiştirici veya daha önce eklenebilir `public` .  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Çıktının değiştirilmediğini doğrulamak için programı yeniden çalıştırın. Ayrıca uyarının artık göründüğünü doğrulayın. Kullanarak `new` , değiştirdiği üyenin, temel sınıftan devralınan bir üyeyi gizlediğini fark edersiniz. Devralma yoluyla ad gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).  
  
 Bu davranışı kullanmanın etkilerine karşı tersine geçmek için `override` aşağıdaki yöntemi öğesine ekleyin `DerivedClass` . `override`Değiştirici veya daha önce eklenebilir `public` .  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 `virtual`Değiştiricisini içindeki tanımına ekleyin `Method1` `BaseClass` . `virtual`Değiştirici veya daha önce eklenebilir `public` .  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Projeyi tekrar çalıştırın. Özellikle aşağıdaki Çıktının son iki satırını görürsünüz.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Değiştiricinin kullanımı, `override` `bcdc` `Method1` içinde tanımlanan yönteme erişim sağlar `DerivedClass` . Genellikle, devralma hiyerarşilerindeki istenen davranıştır. Türetilmiş sınıftan oluşturulan değerlere sahip nesnelerin türetilmiş sınıfta tanımlanan yöntemleri kullanmasını istiyorsunuz. `override`Temel sınıf yöntemini genişletmek için bu davranışı kullanarak elde edersiniz.  
  
 Aşağıdaki kod tam örneği içerir.  
  
```csharp  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
```  
  
 Aşağıdaki örnek farklı bağlamdaki benzer davranışı gösterir. Örnek üç sınıfı tanımlar: adlı bir temel sınıf `Car` ve ondan türetilmiş iki sınıf `ConvertibleCar` ve `Minivan` . Temel sınıf bir yöntemi içerir `DescribeCar` . Yöntemi, bir araba için temel bir açıklama görüntüler ve daha sonra `ShowDetails` ek bilgi sağlamak için çağırır. Üç sınıfın her biri bir yöntemi tanımlar `ShowDetails` . `new`Değiştirici sınıfında tanımlamak için kullanılır `ShowDetails` `ConvertibleCar` . `override`Değiştirici sınıfında tanımlamak için kullanılır `ShowDetails` `Minivan` .  
  
```csharp  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 Örnek, hangi sürümünün çağrıldığını sınar `ShowDetails` . Aşağıdaki yöntem, `TestCars1` her sınıfın bir örneğini bildirir ve ardından `DescribeCar` her bir örnek üzerinde çağırır.  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 `TestCars1`Aşağıdaki çıktıyı üretir. Özellikle `car2` , beklendikleriniz olmayan büyük olasılıkla için sonuçları görebilirsiniz. Nesnenin türü, `ConvertibleCar` ancak `DescribeCar` `ShowDetails` `ConvertibleCar` Bu yöntem değiştirici `new` değil değiştiriciyle bildirildiği için sınıfında tanımlanan sürümüne erişmez `override` . Sonuç olarak, bir `ConvertibleCar` nesnesi bir nesneyle aynı açıklamayı görüntüler `Car` . `car3`Bir nesnesi olan için sonuçlarını kontrast `Minivan` . Bu durumda, `ShowDetails` sınıfında belirtilen yöntem, `Minivan` `ShowDetails` sınıfında belirtilen yöntemi geçersiz kılar `Car` ve görüntülenen açıklama bir mini Van 'yi tanımlar.  
  
```csharp  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 `TestCars2`türü olan nesnelerin bir listesini oluşturur `Car` . Nesnelerin değerleri `Car` ,, `ConvertibleCar` ve `Minivan` sınıflarından oluşturulur. `DescribeCar`, listedeki her öğe için çağrılır. Aşağıdaki kod tanımını gösterir `TestCars2` .  
  
```csharp  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
```  
  
 Aşağıdaki çıktı görüntülenir. Bunun, tarafından görüntülenen çıktıyla aynı olduğuna dikkat edin `TestCars1` . Sınıfının yöntemi, nesne türünün ' de olduğu gibi, veya ' de olduğu gibi `ShowDetails` `ConvertibleCar` çağrılmaz `ConvertibleCar` `TestCars1` `Car` `TestCars2` . Buna karşılık, `car3` `ShowDetails` `Minivan` tür veya tür içerip içermediğini her iki durumda da sınıfından yöntemini çağırır `Minivan` `Car` .  
  
```csharp  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 Yöntemini `TestCars3` `TestCars4` doldurun ve örnek. Bu yöntemler `ShowDetails` , önce türü ve () olan olarak belirtilen nesnelerden `ConvertibleCar` `Minivan` `TestCars3` , daha sonra türü () olan olarak belirtilen nesnelerden doğrudan `Car` çağrı yapılır `TestCars4` . Aşağıdaki kod bu iki yöntemi tanımlar.  
  
```csharp  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
```  
  
 Yöntemler, bu konudaki ilk örnekteki sonuçlara karşılık gelen aşağıdaki çıktıyı üretir.  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 Aşağıdaki kod, tüm projeyi ve çıktısını gösterir.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [Soyut](../../language-reference/keywords/abstract.md)
