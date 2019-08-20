---
title: Geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını C# bilme-Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 00751cd8eac7979fe94d890ddeb7d13edb233f9e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596478"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)

İçinde C#, türetilmiş bir sınıftaki bir yöntem, temel sınıftaki bir yöntemle aynı ada sahip olabilir. Yöntemlerinin [New](../../language-reference/keywords/new-modifier.md) ve [override](../../language-reference/keywords/override.md) anahtar sözcüklerini kullanarak nasıl etkileşime gireceğini belirtebilirsiniz. `virtual` `new` Değiştirici, temel sınıf yöntemini genişletir ve değiştirici, erişilebilir bir temel sınıf yöntemini gizler. `override` Fark, bu konudaki örneklerde gösterilmiştir.  
  
 Konsol uygulamasında, aşağıdaki iki sınıfı `BaseClass` bildirin ve. `DerivedClass` `DerivedClass`öğesinden `BaseClass`devralır.  
  
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
  
 Yönteminde, ve `bc` değişkenlerinibildirin.`bcdc` `dc` `Main`  
  
- `bc`türündedir `BaseClass`ve değeri türündedir `BaseClass`.  
  
- `dc`türündedir `DerivedClass`ve değeri türündedir `DerivedClass`.  
  
- `bcdc`türündedir `BaseClass`ve değeri türündedir `DerivedClass`. Bu, dikkat edilmesi gereken değişkendir.  
  
 Ve `bc` türüolduğundan`BaseClass`, atama kullanmadığınız müddetçe yalnızca doğrudan erişim `Method1`sağlayabilir. `bcdc` Değişken `dc` , `Method1` ve ' `Method2`a erişebilir. Bu ilişkiler aşağıdaki kodda gösterilmiştir.  
  
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
  
 Ardından, aşağıdaki `Method2` yöntemi öğesine `BaseClass`ekleyin. Bu yöntemin imzası içindeki `Method2` `DerivedClass`yönteminin imzasıyla eşleşir.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Artık `BaseClass` bir `BaseClass` `bc` `bcdc`yöntemi olduğundan, aşağıdaki kodda gösterildiği gibi, değişkenler için ikinci bir çağırma açıklaması eklenebilir. `Method2`  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Projeyi derlediğinizde, içinde `Method2` `BaseClass` yönteminin eklenmesi bir uyarıya neden olur. Uyarı, içindeki `DerivedClass` yönteminin içindeki `Method2` `Method2` yöntemigizlediğinibelirtir`BaseClass`. Bu sonuca neden olmak istiyorsanız, `new` `Method2` tanımda anahtar sözcüğünü kullanmanız önerilir. Alternatif olarak, uyarıyı çözümlemek için `Method2` yöntemlerden birini yeniden adlandırabilirsiniz, ancak her zaman pratik değildir.  
  
 Eklemeden `new`önce, ek çağırma deyimleri tarafından üretilen çıktıyı görmek için programı çalıştırın. Aşağıdaki sonuçlar görüntülenir.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` Anahtar sözcüğü, bu çıktıyı üreten ilişkileri korur, ancak uyarıyı bastırır. Türüne `BaseClass` sahip değişkenler `BaseClass`, üyelerine erişmeye devam eder ve türüne `DerivedClass` sahip olan değişken ilk olarak `DerivedClass` üyelere erişmeye devam eder ve öğesinden `BaseClass`devralınan üyeleri göz önünde bulundurun.  
  
 Uyarıyı bastırmak için, aşağıdaki kodda gösterildiği `new` gibi değiştiricisini `Method2` içindeki `DerivedClass`tanımına ekleyin. Değiştirici veya `public`daha önce eklenebilir.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Çıktının değiştirilmediğini doğrulamak için programı yeniden çalıştırın. Ayrıca uyarının artık göründüğünü doğrulayın. Kullanarak `new`, değiştirdiği üyenin, temel sınıftan devralınan bir üyeyi gizlediğini fark edersiniz. Devralma yoluyla ad gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).  
  
 Bu davranışı kullanmanın `override`etkilerine karşı tersine geçmek için aşağıdaki yöntemi öğesine `DerivedClass`ekleyin. Değiştirici veya daha önce eklenebilir. `public` `override`  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 `virtual` Değiştiricisini`Method1` içindeki tanımına`BaseClass`ekleyin. Değiştirici veya daha önce eklenebilir. `public` `virtual`  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Projeyi yeniden çalıştırın. Özellikle aşağıdaki Çıktının son iki satırını görürsünüz.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 `override` Değiştiricinin kullanımı, içinde `bcdc` `Method1` tanımlanan`DerivedClass`yönteme erişim sağlar. Genellikle, devralma hiyerarşilerindeki istenen davranıştır. Türetilmiş sınıftan oluşturulan değerlere sahip nesnelerin türetilmiş sınıfta tanımlanan yöntemleri kullanmasını istiyorsunuz. Temel sınıf yöntemini genişletmek için bu `override` davranışı kullanarak elde edersiniz.  
  
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
  
 Aşağıdaki örnek farklı bağlamdaki benzer davranışı gösterir. Örnek üç sınıfı tanımlar: adlı `Car` bir temel sınıf ve ondan türetilmiş `ConvertibleCar` iki sınıf ve `Minivan`. Temel sınıf bir `DescribeCar` yöntemi içerir. Yöntemi, bir araba için temel bir açıklama görüntüler ve daha sonra ek `ShowDetails` bilgi sağlamak için çağırır. Üç sınıfın her biri bir `ShowDetails` yöntemi tanımlar. Değiştirici sınıfında tanımlamak `ShowDetails` için kullanılır. `ConvertibleCar` `new` Değiştirici sınıfında tanımlamak `ShowDetails` için kullanılır. `Minivan` `override`  
  
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
  
 Örnek, hangi sürümünün `ShowDetails` çağrıldığını sınar. Aşağıdaki yöntem `TestCars1`, her sınıfın bir örneğini bildirir ve ardından her bir örnek üzerinde çağırır `DescribeCar` .  
  
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
  
 `TestCars1`Aşağıdaki çıktıyı üretir. Özellikle, beklendikleriniz `car2`olmayan büyük olasılıkla için sonuçları görebilirsiniz. `ConvertibleCar`Nesnenin `new` türü, `DescribeCar` ancak bu yöntem değiştirici değil `ShowDetails` `ConvertibleCar` değiştiriciylebildirildiğiiçinsınıfındatanımlanan`override` sürümüne erişmez. Sonuç olarak, `ConvertibleCar` bir nesnesi bir `Car` nesneyle aynı açıklamayı görüntüler. `car3` Bir`Minivan` nesnesi olan için sonuçlarını kontrast. Bu `ShowDetails` durumda, `Minivan` sınıfında belirtilen yöntem, `Car` sınıfında belirtilen `ShowDetails` yöntemi geçersiz kılar ve görüntülenen açıklama bir mini Van 'yi tanımlar.  
  
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
  
 `TestCars2`türü `Car`olan nesnelerin bir listesini oluşturur. Nesnelerin değerleri `Car`, `ConvertibleCar`, ve `Minivan` sınıflarından oluşturulur. `DescribeCar`, listedeki her öğe için çağrılır. Aşağıdaki kod tanımını `TestCars2`gösterir.  
  
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
  
 Aşağıdaki çıktı görüntülenir. Bunun, tarafından `TestCars1`görüntülenen çıktıyla aynı olduğuna dikkat edin. `ShowDetails` `Car`Sınıfının yöntemi `TestCars2`, nesne `ConvertibleCar`türünün ' de olduğu gibi, veya ' de olduğu gibi çağrılmaz. `TestCars1` `ConvertibleCar` Buna karşılık `car3` , tür `ShowDetails` `Minivan` veyatür`Car`içerip içermediğini her iki durumda da sınıfından yöntemini çağırır. `Minivan`  
  
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
  
 Yöntemini `TestCars3` doldurun `TestCars4` ve örnek. Bu yöntemler, `ShowDetails` önce türü `ConvertibleCar` ve `Minivan` (`TestCars3`) olan olarak belirtilen nesnelerden, daha sonra türü `Car` (`TestCars4`) olan olarak belirtilen nesnelerden doğrudan çağrı yapılır. Aşağıdaki kod bu iki yöntemi tanımlar.  
  
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
