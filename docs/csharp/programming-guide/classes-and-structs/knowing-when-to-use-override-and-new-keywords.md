---
title: Geçersiz kılma ve yeni anahtar sözcüklerle - ne zaman kullanılacağını bilme C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: d44d8d0143d366117a24495df3fa8a18f893ebb3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244745"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)
C# ' ta türetilen bir sınıfta bir yöntem temel sınıfta bir yöntem adıyla aynı olabilir. Yöntemleri kullanarak etkileşimini belirtebilirsiniz [yeni](../../../csharp/language-reference/keywords/new.md) ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcükleri. `override` Değiştiricisi *genişletir* temel sınıf yöntemini ve `new` değiştiricisi *gizler* bu. Fark, bu konudaki örneklerde gösterilmiştir.  
  
 Bir konsol uygulamasında aşağıdaki iki sınıf bildirme `BaseClass` ve `DerivedClass`. `DerivedClass` devralınan `BaseClass`.  
  
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
  
 İçinde `Main` yöntemi, değişkenleri `bc`, `dc`, ve `bcdc`.  
  
-   `bc` tür `BaseClass`, ve değeri türü `BaseClass`.  
  
-   `dc` tür `DerivedClass`, ve değeri türü `DerivedClass`.  
  
-   `bcdc` tür `BaseClass`, ve değeri türü `DerivedClass`. Değişken dikkat edilmesi gereken budur.  
  
 Çünkü `bc` ve `bcdc` türüne sahip `BaseClass`, yalnızca doğrudan erişebilir `Method1`atama kullandığınız sürece. Değişken `dc` hem erişim `Method1` ve `Method2`. Bu ilişkiler aşağıdaki kodda gösterilmiştir.  
  
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
  
 Ardından, aşağıdaki ekleyin `Method2` yönteme `BaseClass`. Bu yöntemin imzası imzası eşleşen `Method2` yönteminde `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Çünkü `BaseClass` artık bir `Method2` yönteminde deyim çağırma ikinci eklenebilir için `BaseClass` değişkenleri `bc` ve `bcdc`aşağıdaki kodda gösterildiği gibi.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Proje oluşturduğunuzda, gördüğünüz eklenmesini `Method2` yöntemi `BaseClass` bir uyarısına neden olur. Uyarı bildiren `Method2` yönteminde `DerivedClass` gizler `Method2` yönteminde `BaseClass`. Kullanılacak kopyaladınız `new` anahtar sözcüğünü `Method2` sonucunda ortaya çıkan neden istiyorsanız, tanım. Alternatif olarak, aşağıdakilerden birini adlandırabilirsiniz `Method2` uyarı ancak çözmek için yöntemleri değil her zaman pratik.  
  
 Eklemeden önce `new`, ek çağrıyı yapan ifadeler tarafından üretilen çıktıyı görmek için programını çalıştırın. Aşağıdaki sonuçları görüntülenir.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` Anahtar sözcüğü bu çıkışı üreten ilişkileri korur, ancak uyarı bastırır. Türüne sahip değişkenler `BaseClass` üyelerinin erişmeye devam `BaseClass`ve türünde değişken `DerivedClass` üyeleri erişmeye devam `DerivedClass` ilk olarak ve ardından öğesinden devralınan üyelere dikkate alınması gereken `BaseClass`.  
  
 Uyarıyı bastırmak için ekleme `new` tanımının değiştiricisi `Method2` içinde `DerivedClass`aşağıdaki kodda gösterildiği gibi. Önce veya sonra değiştiricisi eklenebilir `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Çıkış değiştirilmedi yeniden doğrulamak için programı çalıştırın. Ayrıca uyarı artık göründüğünü doğrulayın. Kullanarak `new`, değiştirdiği üyesi temel sınıftan devralınan üyeyi gizler haberdar olduğunuzu çiftidir. Devralma üzerinden ad gizleme hakkında daha fazla bilgi için bkz: [new değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Bu davranış kullanmanın etkileri için buna karşılık `override`, aşağıdaki yöntemi ekleyin `DerivedClass`. `override` Değiştiricisi eklenebilir, önce veya sonra `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Ekleme `virtual` tanımının değiştiricisi `Method1` içinde `BaseClass`. `virtual` Değiştiricisi eklenebilir, önce veya sonra `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Projeyi yeniden çalıştırın. Aşağıdaki çıktı özellikle son iki satırlık dikkat edin.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Kullanımını `override` değiştirici etkinleştirir `bcdc` erişimi `Method1` tanımlanan yöntemi `DerivedClass`. Genellikle, devralma hiyerarşilerini istenen davranışı olmasıdır. Türetilmiş sınıftan türetilen bir sınıfta tanımlanan yöntemleri kullanmak için oluşturduğunuz değerlerine sahip nesneleri kullanmanız gerekir. Kullanarak bu davranışı elde `override` temel sınıf yöntemini genişletmek için.  
  
 Aşağıdaki kod tam örneği içermektedir.  
  
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
  
 Aşağıdaki örnek, farklı bir bağlamda benzer bir davranış gösterir. Örnek üç sınıf tanımlar: adlı bir temel sınıf `Car` ve kendisinden üretilmiş iki sınıf `ConvertibleCar` ve `Minivan`. Taban sınıfı içeren bir `DescribeCar` yöntemi. Yöntemi, bir araba temel açıklamasını görüntüler ve ardından çağırır `ShowDetails` ek bilgi sağlamak için. Üç sınıfların her birini tanımlayan bir `ShowDetails` yöntemi. `new` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `ConvertibleCar` sınıfı. `override` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `Minivan` sınıfı.  
  
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
  
 Örnek hangi sürümünün testlerini `ShowDetails` çağrılır. Aşağıdaki yöntem `TestCars1`her sınıfın bir örneği bildirir ve ardından çağırır `DescribeCar` her örneğinde.  
  
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
  
 `TestCars1` aşağıdaki çıktıyı üretir. Sonuçları özellikle dikkat edin `car2`, büyük olasılıkla olduğu beklediğiniz değil. Nesne türü `ConvertibleCar`, ancak `DescribeCar` sürümünü erişmez `ShowDetails` içinde tanımlanan `ConvertibleCar` bu yöntem ile bildirildiğinden sınıf `new` değiştiricisi değil `override` değiştiricisi. Sonuç olarak, bir `ConvertibleCar` nesne görüntüler aynı açıklama olarak bir `Car` nesne. Sonuçları Karşıtlık `car3`, olduğu bir `Minivan` nesne. Bu durumda, `ShowDetails` bölümünde bildirilen yöntemi `Minivan` sınıf geçersiz kılmalarını `ShowDetails` bölümünde bildirilen yöntemi `Car` sınıfı ve görüntülenen açıklamayı bir minivan açıklar.  
  
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
  
 `TestCars2` türü olan nesnelerin bir listesini oluşturur `Car`. Nesne değerlerini örneği oluşturulur `Car`, `ConvertibleCar`, ve `Minivan` sınıfları. `DescribeCar` Listedeki her öğe üzerinde çağrılır. Aşağıdaki kod tanımını gösterir `TestCars2`.  
  
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
  
 Aşağıdaki çıktı görüntülenir. Tarafından görüntülenen çıktı ile aynı olduğunu fark `TestCars1`. `ShowDetails` Yöntemi `ConvertibleCar` sınıfı çağrılmaz; nesne türü olmasına bakılmaksızın `ConvertibleCar`, olarak `TestCars1`, veya `Car`, olarak `TestCars2`. Buna karşılık, `car3` çağrıları `ShowDetails` yönteminden `Minivan` türüne sahip olup olmadığını her iki durumda da, sınıf `Minivan` veya türü `Car`.  
  
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
  
 Yöntemleri `TestCars3` ve `TestCars4` örnek tamamlayın. Bu yöntemleri çağırmak `ShowDetails` doğrudan, ilk nesnelerden bildirilen türü olmasını `ConvertibleCar` ve `Minivan` (`TestCars3`), ardından türü için bildirilen nesnelerden `Car` (`TestCars4`). Aşağıdaki kod, bu iki yöntem tanımlar.  
  
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
  
 Yöntemler, bu konudaki ilk örnekte karşılık gelen sonuçları aşağıdaki çıktıyı üretir.  
  
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
  
 Aşağıdaki kod tam projeyi ve çıktısını gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
- [base](../../../csharp/language-reference/keywords/base.md)  
- [abstract](../../../csharp/language-reference/keywords/abstract.md)
