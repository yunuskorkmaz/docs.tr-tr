---
title: Geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını C# bilme-Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 0a209b9522202649765654013fdc3a468913c6b1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714786"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)

İçinde C#, türetilmiş bir sınıftaki bir yöntem, temel sınıftaki bir yöntemle aynı ada sahip olabilir. Yöntemlerinin [New](../../language-reference/keywords/new-modifier.md) ve [override](../../language-reference/keywords/override.md) anahtar sözcüklerini kullanarak nasıl etkileşime gireceğini belirtebilirsiniz. `override` değiştirici temel sınıf `virtual` yöntemini *genişletir* ve `new` değiştiricisi erişilebilir bir temel sınıf yöntemini *gizler* . Fark, bu konudaki örneklerde gösterilmiştir.  
  
 Konsol uygulamasında, `BaseClass` ve `DerivedClass`aşağıdaki iki sınıfı bildirin. `DerivedClass` `BaseClass`devralır.  
  
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
  
 `Main` yönteminde, değişkenleri `bc`, `dc`ve `bcdc`bildirin.  
  
- `bc` `BaseClass`türüdür ve değeri `BaseClass`türündedir.  
  
- `dc` `DerivedClass`türüdür ve değeri `DerivedClass`türündedir.  
  
- `bcdc` `BaseClass`türüdür ve değeri `DerivedClass`türündedir. Bu, dikkat edilmesi gereken değişkendir.  
  
 `bc` ve `bcdc` tür `BaseClass`olduğundan, atama kullanmadığınız müddetçe yalnızca `Method1`doğrudan erişim sağlayabilir. Değişken `dc`, hem `Method1` hem de `Method2`erişebilir. Bu ilişkiler aşağıdaki kodda gösterilmiştir.  
  
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
  
 Sonra, `BaseClass`için aşağıdaki `Method2` yöntemi ekleyin. Bu yöntemin imzası, `DerivedClass``Method2` yönteminin imzasıyla eşleşir.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 `BaseClass` artık `Method2` bir yöntemi olduğundan, aşağıdaki kodda gösterildiği gibi `BaseClass` değişkenleri `bc` ve `bcdc`için ikinci bir çağrı ekstresi eklenebilir.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Projeyi derlediğinizde `Method2` yönteminin `BaseClass` bir uyarıya neden olduğunu görürsünüz. Uyarı, `DerivedClass` `Method2` yönteminin `BaseClass``Method2` yöntemini gizlediğini belirtir. Bu sonuca neden olmak istiyorsanız `Method2` tanımında `new` anahtar sözcüğünü kullanmanız önerilir. Alternatif olarak, uyarıyı çözümlemek için `Method2` yöntemlerinden birini yeniden adlandırabilirsiniz, ancak bu her zaman pratik değildir.  
  
 `new`eklemeden önce, ek çağırma deyimleri tarafından üretilen çıktıyı görmek için programı çalıştırın. Aşağıdaki sonuçlar görüntülenir.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` anahtar sözcüğü, bu çıktıyı üreten ilişkileri korur, ancak uyarıyı bastırır. Türü `BaseClass` olan değişkenler `BaseClass`üyelerine erişmeye devam eder ve tür `DerivedClass` olan değişken, önce `DerivedClass` üyelere erişmeye devam eder ve ardından `BaseClass`devralınmış üyeleri göz önüne alın.  
  
 Uyarıyı bastırmak için, aşağıdaki kodda gösterildiği gibi `new` değiştiricisini `DerivedClass``Method2` tanımına ekleyin. Değiştirici, `public`önce veya sonra eklenebilir.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Çıktının değiştirilmediğini doğrulamak için programı yeniden çalıştırın. Ayrıca uyarının artık göründüğünü doğrulayın. `new`kullanarak, değiştirdiği üyenin, temel sınıftan devralınan bir üyeyi gizlediğini unutmayın. Devralma yoluyla ad gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).  
  
 Bu davranışı `override`kullanmanın etkilerinin aksine, `DerivedClass`için aşağıdaki yöntemi ekleyin. `override` değiştiricisi `public`önce veya sonra eklenebilir.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 `virtual` değiştiricisini `BaseClass``Method1` tanımına ekleyin. `virtual` değiştiricisi `public`önce veya sonra eklenebilir.  
  
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
  
 `override` değiştiricisinin kullanımı, `bcdc` `DerivedClass`tanımlanmış `Method1` yöntemine erişmesini sağlar. Genellikle, devralma hiyerarşilerindeki istenen davranıştır. Türetilmiş sınıftan oluşturulan değerlere sahip nesnelerin türetilmiş sınıfta tanımlanan yöntemleri kullanmasını istiyorsunuz. Temel sınıf yöntemini genişletmek için `override` kullanarak bu davranışı elde edersiniz.  
  
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
  
 Aşağıdaki örnek farklı bağlamdaki benzer davranışı gösterir. Örnek üç sınıfı tanımlar: `Car` adlı bir temel sınıf ve bundan türetilmiş iki sınıf, `ConvertibleCar` ve `Minivan`. Temel sınıf bir `DescribeCar` yöntemi içerir. Yöntemi, bir araba için temel bir açıklama görüntüler ve daha sonra ek bilgi sağlamak için `ShowDetails` çağırır. Üç sınıfın her biri bir `ShowDetails` yöntemi tanımlar. `new` değiştiricisi `ConvertibleCar` sınıfında `ShowDetails` tanımlamak için kullanılır. `override` değiştiricisi `Minivan` sınıfında `ShowDetails` tanımlamak için kullanılır.  
  
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
  
 Örnek, hangi `ShowDetails` sürümünün çağrıldığını sınar. Aşağıdaki yöntem `TestCars1`, her sınıfın bir örneğini bildirir ve sonra her bir örnekteki `DescribeCar` çağırır.  
  
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
  
 `TestCars1` aşağıdaki çıktıyı üretir. Büyük olasılıkla beklendikleriniz olmayan `car2`için sonuçlara dikkat edin. Nesnenin türü `ConvertibleCar`, ancak bu yöntem `new` değiştiricisiyle değil `override` değiştiriciyle bildirildiği için, `DescribeCar` `ConvertibleCar` sınıfında tanımlanan `ShowDetails` sürümüne erişemez. Sonuç olarak, bir `ConvertibleCar` nesnesi aynı açıklamayı bir `Car` nesnesi ile görüntüler. Bir `Minivan` nesnesi olan `car3`için sonuçları kontrast. Bu durumda, `Minivan` sınıfında belirtilen `ShowDetails` yöntemi `Car` sınıfında belirtilen `ShowDetails` yöntemini geçersiz kılar ve görüntülenen açıklama bir mini Van 'yi tanımlar.  
  
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
  
 `TestCars2`, `Car`türüne sahip nesnelerin bir listesini oluşturur. Nesnelerin değerleri `Car`, `ConvertibleCar`ve `Minivan` sınıflarından oluşturulur. `DescribeCar`, listedeki her öğe için çağrılır. Aşağıdaki kod `TestCars2`tanımını gösterir.  
  
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
  
 Aşağıdaki çıktı görüntülenir. `TestCars1`tarafından görüntülenen çıktıyla aynı olduğuna dikkat edin. `ConvertibleCar` sınıfının `ShowDetails` yöntemi, nesnenin türünün `TestCars1`veya `Car`gibi `TestCars2`gibi `ConvertibleCar`olmasına bakılmaksızın çağrılmaz. Buna karşılık `car3`, `ShowDetails` yöntemini her iki durumda da `Minivan` sınıfından çağırır `Minivan` veya `Car`yazın.  
  
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
  
 Yöntemler `TestCars3` ve `TestCars4` örneğini tamamlar. Bu yöntemler, öncelikle tür `ConvertibleCar` ve `Minivan` (`TestCars3`) sahip olduğu belirtilen nesnelerden, daha sonra tür `Car` (`TestCars4`) sahip olarak belirtilen nesnelerden `ShowDetails`. Aşağıdaki kod bu iki yöntemi tanımlar.  
  
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
- [Sınıflar ve Yapılar](./index.md)
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [abstract](../../language-reference/keywords/abstract.md)
