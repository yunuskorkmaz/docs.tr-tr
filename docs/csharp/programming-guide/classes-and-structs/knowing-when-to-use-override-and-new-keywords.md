---
title: Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 61bfa87b7aaa7c17d4ba67c69fa1e57ee7415dc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)
C# ' ta türetilmiş bir sınıf yönteminde taban sınıf içinde aynı adı taşıyan bir yöntem olabilir. Yöntemleri kullanarak nasıl etkileşim belirtebilirsiniz [yeni](../../../csharp/language-reference/keywords/new.md) ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcükler. `override` Değiştiricisi *genişletir* temel sınıf yöntemi ve `new` değiştiricisi *gizler* onu. Bu konudaki örnekler fark gösterilmiştir.  
  
 Bir konsol uygulamasında aşağıdaki iki sınıf bildirme `BaseClass` ve `DerivedClass`. `DerivedClass` öğesinden devralınan `BaseClass`.  
  
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
  
 İçinde `Main` yöntemi, değişkenleri bildirin `bc`, `dc`, ve `bcdc`.  
  
-   `bc` tür `BaseClass`, ve türü değeri olduğu `BaseClass`.  
  
-   `dc` tür `DerivedClass`, ve türü değeri olduğu `DerivedClass`.  
  
-   `bcdc` tür `BaseClass`, ve türü değeri olduğu `DerivedClass`. Bu dikkat edilmesi gereken değişkenidir.  
  
 Çünkü `bc` ve `bcdc` türüne sahip `BaseClass`, yalnızca doğrudan erişebilirsiniz `Method1`sürece atama kullanın. Değişken `dc` her ikisi de erişebilir `Method1` ve `Method2`. Bu ilişkileri aşağıdaki kodda gösterilir.  
  
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
  
 Ardından, aşağıdaki ekleyin `Method2` yöntemine `BaseClass`. Bu yöntem imzası imzası eşleşen `Method2` yönteminde `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Çünkü `BaseClass` artık bir `Method2` yöntemi, ikinci bir arama ifade eklenebilir için `BaseClass` değişkenleri `bc` ve `bcdc`aşağıdaki kodda gösterildiği gibi.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Bkz, projeyi derlerken eklenmesi `Method2` yönteminde `BaseClass` bir uyarı neden olur. Uyarı bildiren `Method2` yönteminde `DerivedClass` gizler `Method2` yönteminde `BaseClass`. Kullanmak için önerilir `new` anahtar sözcük `Method2` sonucunda ortaya çıkan neden istiyorsanız tanımı. Alternatif olarak, aşağıdakilerden birini adlandırabilirsiniz `Method2` uyarı ancak çözmek için yöntemleri değil her zaman pratik.  
  
 Eklemeden önce `new`, ek arama deyimleri tarafından üretilen çıkış görmek için programını çalıştırın. Aşağıdaki sonuçları görüntülenir.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` Anahtar sözcüğü, bu çıkış üretemeyecek ilişkileri korur, ancak uyarı gizler. Türüne sahip değişkenler `BaseClass` üyelerini erişmeye devam `BaseClass`, türüne sahip değişkeni `DerivedClass` üyeleri erişmeye devam `DerivedClass` ilk, ardından devralınan üyeler dikkate alınması gereken `BaseClass`.  
  
 Uyarıyı gizlemek için ekleme `new` tanımını değiştiriciyi `Method2` içinde `DerivedClass`aşağıdaki kodda gösterildiği gibi. Değiştirici önce veya sonra eklenebilir `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Çıktı değişmediğini yeniden doğrulamak için programını çalıştırın. Ayrıca uyarı artık göründüğünü doğrulayın. Kullanarak `new`, değiştirdiği üye temel sınıfından devralınan bir üye gizler kullanan çiftidir. Devralma yoluyla adı gizleme hakkında daha fazla bilgi için bkz: [new değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Bu davranış kullanmanın etkileri için buna karşılık `override`, aşağıdaki yöntemi ekleyin `DerivedClass`. `override` Önce veya sonra değiştiricisi eklenebilir `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Ekleme `virtual` tanımını değiştiriciyi `Method1` içinde `BaseClass`. `virtual` Önce veya sonra değiştiricisi eklenebilir `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Projeyi tekrar çalıştırın. Aşağıdaki çıkış özellikle son iki satırlık dikkat edin.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Kullanımını `override` değiştiricisi etkinleştirir `bcdc` erişimi `Method1` tanımlanan yöntemi `DerivedClass`. Genellikle, başka bir deyişle istenen davranışı devralma Hiyerarşiler. Türetilmiş sınıfından türetilen sınıfta tanımlanan yöntemler kullanmayı oluşturulan değerlerine sahip nesneleri istiyor. Kullanarak bu davranışı elde `override` temel sınıf yöntemi genişletmek için.  
  
 Aşağıdaki kod, tam örnek içerir.  
  
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
  
 Aşağıdaki örnek, farklı bir bağlamda benzer davranış gösterilmektedir. Örnek üç sınıf tanımlar: adlı bir temel sınıf `Car` ve bu sınıftan türetilen iki sınıf `ConvertibleCar` ve `Minivan`. Taban sınıfı içeren bir `DescribeCar` yöntemi. Yöntemi, bir araba temel açıklamasını görüntüler ve çağırır `ShowDetails` ek bilgi sağlamak için. Her üç sınıfların tanımlayan bir `ShowDetails` yöntemi. `new` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `ConvertibleCar` sınıfı. `override` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `Minivan` sınıfı.  
  
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
  
 Örnek hangi sürümünün testleri `ShowDetails` olarak adlandırılır. Aşağıdaki yöntem `TestCars1`her sınıfının bir örneği bildirir ve ardından çağırır `DescribeCar` her örneğindeki.  
  
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
  
 `TestCars1` şu çıkışı üretir. Sonuçları özellikle dikkat edin `car2`, büyük olasılıkla olduğu beklediğinize değil. Nesne türü `ConvertibleCar`, ancak `DescribeCar` sürümü erişmez `ShowDetails` içinde tanımlanan `ConvertibleCar` bu yöntem ile bildirildiğinden sınıf `new` değiştiricisi, değil `override` değiştiricisi. Sonuç olarak, bir `ConvertibleCar` nesne görüntüler aynı açıklama olarak bir `Car` nesnesi. Sonuçlar için Karşıtlık `car3`, olduğu bir `Minivan` nesnesi. Bu durumda, `ShowDetails` içinde bildirilen yöntemi `Minivan` geçersiz kılmaları sınıf `ShowDetails` içinde bildirilen yöntemi `Car` sınıfı ve görüntülenen açıklama bir minivan açıklar.  
  
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
  
 `TestCars2` türüne sahip nesnelerin bir listesini oluşturur `Car`. Değerlerin nesnelerin örneği oluşturulmadan `Car`, `ConvertibleCar`, ve `Minivan` sınıfları. `DescribeCar` Listenin her öğesinin adı verilir. Aşağıdaki kod tanımını gösterir `TestCars2`.  
  
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
  
 Aşağıdaki çıktısı görüntülenir. Tarafından görüntülenen çıktı ile aynı olduğunu fark `TestCars1`. `ShowDetails` Yöntemi `ConvertibleCar` sınıfı çağrılmaz, nesne türü olmasına bakılmaksızın `ConvertibleCar`, olarak `TestCars1`, veya `Car`, olarak `TestCars2`. Buna karşılık, `car3` çağrıları `ShowDetails` yönteminden `Minivan` türüne sahip olup olmadığını her iki durumda da sınıf `Minivan` veya türü `Car`.  
  
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
  
 Yöntemleri `TestCars3` ve `TestCars4` tam örnek. Bu yöntemleri `ShowDetails` doğrudan ilk nesnelerden bildirilen türün `ConvertibleCar` ve `Minivan` (`TestCars3`), ardından türün bildirilen nesnelerinden `Car` (`TestCars4`). Aşağıdaki kod bu iki yöntem tanımlar.  
  
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
  
 Yöntemleri, bu konunun ilk örneğindeki sonuçları karşılık gelen aşağıdaki çıktı üretir.  
  
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
  
 Aşağıdaki kod, tam projeyi ve çıktısını gösterir.  
  
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [base](../../../csharp/language-reference/keywords/base.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)
