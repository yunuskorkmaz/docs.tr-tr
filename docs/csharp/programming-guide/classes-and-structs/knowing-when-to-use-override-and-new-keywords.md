---
title: Override ve Yeni Anahtar Kelimeler Ne Zaman Kullanılacağını Bilmek - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 493c6c5f5bf47c6b2cd140ac0f6922f91ca4252b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170266"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)

C#'da, türemiş bir sınıftaki bir yöntem, taban sınıftaki yöntemle aynı ada sahip olabilir. [Yeni](../../language-reference/keywords/new-modifier.md) ve [geçersiz kılma](../../language-reference/keywords/override.md) anahtar kelimelerini kullanarak yöntemlerin nasıl etkileşimde olduğunu belirtebilirsiniz. `override` Değiştirici temel sınıf `virtual` yöntemini *genişletir* `new` ve değiştirici erişilebilir bir taban sınıf *yöntemini gizler.* Fark bu konudaki örneklerde gösterilmiştir.  
  
 Konsol uygulamasında, aşağıdaki iki sınıfı `BaseClass` bildirin ve `DerivedClass`. `DerivedClass`'den `BaseClass`devralır.  
  
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
  
 Yöntemde, `Main` `bc`değişkenleri bildirin , `dc`, ve `bcdc`.  
  
- `bc`türündedir `BaseClass`ve değeri türdedir. `BaseClass`  
  
- `dc`türündedir `DerivedClass`ve değeri türdedir. `DerivedClass`  
  
- `bcdc`türündedir `BaseClass`ve değeri türdedir. `DerivedClass` Bu dikkat etmek için değişkendir.  
  
 Çünkü `bc` `bcdc` ve `BaseClass`türü var , `Method1`onlar sadece doğrudan erişebilirsiniz , döküm kullanmadığınız sürece. Değişken `dc` hem `Method1` erişebilir `Method2`hem de. Bu ilişkiler aşağıdaki kodda gösterilir.  
  
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
  
 Ardından, `Method2` `BaseClass`aşağıdaki yöntemi ekleyin. Bu yöntemin imzası yöntemin `Method2` imzası `DerivedClass`ile eşleşir.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Artık `BaseClass` bir `Method2` metodu olduğundan, `BaseClass` değişkenler `bc` için ikinci `bcdc`bir çağrı deyimi eklenebilir ve aşağıdaki kodda gösterildiği gibi.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Projeyi oluşturduğunuzda, `Method2` `BaseClass` yöntemin eklenmesinin bir uyarıya neden olduğunu görürsünüz. Uyarı, yöntemin `Method2` `DerivedClass` yöntemi ' `Method2` nin `BaseClass`' içinde gizler. Bu sonuca neden `new` olmak istiyorsanız, `Method2` tanımdaki anahtar kelimeyi kullanmanız önerilir. Alternatif olarak, uyarıyı `Method2` çözmek için yöntemlerden birini yeniden adlandırabilirsiniz, ancak bu her zaman pratik değildir.  
  
 Eklemeden `new`önce, ek arama ekstreleri tarafından üretilen çıktıyı görmek için programı çalıştırın. Aşağıdaki sonuçlar görüntülenir.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 Anahtar `new` kelime, bu çıktıyı üreten ilişkileri korur, ancak uyarıyı bastırır. `BaseClass` Türü olan değişkenler `BaseClass`üyelerine erişmeye devam eder ve `DerivedClass` türü olan değişken `DerivedClass` önce üyelere erişmeye devam `BaseClass`eder, sonra da 'den devralınan üyeleri dikkate alır.  
  
 Uyarıyı bastırmak için, `new` aşağıdaki kodda gösterildiği `Method2` `DerivedClass`gibi in tanımına değiştirici ekleyin. Değiştirici önce veya sonra `public`eklenebilir.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Çıktının değişmediğini doğrulamak için programı yeniden çalıştırın. Ayrıca, uyarının artık görünmediğini de doğrulayın. Kullanarak, `new`modite ettiği üyenin taban sınıftan devralınan bir üyeyi gizlediğinin farkında olduğunuzu iddia etmiş oluyorsunuz. Devralma yoluyla ad gizleme hakkında daha fazla bilgi için [yeni Değiştirici'ye](../../language-reference/keywords/new-modifier.md)bakın.  
  
 Bu davranışı kullanmanın `override`etkileriyle karşılaştırmak için `DerivedClass`aşağıdaki yöntemi ekleyin. `override` Değiştirici önce veya sonra `public`eklenebilir.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 'nin `virtual` tanımına `Method1` değiştirici `BaseClass`ekleyin. `virtual` Değiştirici önce veya sonra `public`eklenebilir.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Projeyi tekrar çalıştırın. Özellikle aşağıdaki çıktının son iki satırına dikkat edin.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 `override` Değiştiricinin kullanımı, 'de `bcdc` `DerivedClass`tanımlanan `Method1` yönteme erişmenizi sağlar. Genellikle, bu devralma hiyerarşilerinde istenen davranıştır. Türemiş sınıfta tanımlanan yöntemleri kullanmak için türetilmiş sınıftan oluşturulan değerlere sahip nesnelerin kullanılmasını istiyorsunuz. Bu davranışı temel `override` sınıf yöntemini genişletmek için kullanarak elde elabilirsiniz.  
  
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
  
 Aşağıdaki örnek, benzer davranışı farklı bir bağlamda göstermektedir. Örnekte üç sınıf tanımlanır: bir `Car` taban sınıf adlandırılmış ve `ConvertibleCar` `Minivan`ondan türetilen iki sınıf ve . Taban sınıf bir `DescribeCar` yöntem içerir. Yöntem, bir aracın temel açıklamasını görüntüler `ShowDetails` ve daha sonra ek bilgi sağlamak için çağrılar. Üç sınıfın her biri `ShowDetails` bir yöntem tanımlar. `new` Değiştirici `ConvertibleCar` sınıfta tanımlamak `ShowDetails` için kullanılır. `override` Değiştirici `Minivan` sınıfta tanımlamak `ShowDetails` için kullanılır.  
  
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
  
 Örnek, hangi sürümün `ShowDetails` çağrıldığını sınar. Aşağıdaki yöntem, `TestCars1`her sınıfın bir örneğini bildirir `DescribeCar` ve sonra her örneği çağırır.  
  
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
  
 `TestCars1`aşağıdaki çıktıyı üretir. Muhtemelen beklediğiniz `car2`gibi değil, özellikle sonuçları dikkat edin. Nesnenin `ConvertibleCar` `DescribeCar` türü, ancak bu yöntem `ShowDetails` `ConvertibleCar` `new` `override` değiştirici değil, değiştirici ile bildirilir, çünkü sınıfta tanımlanan sürümü erişmiyor. Sonuç olarak, `ConvertibleCar` bir nesne nesneyle `Car` aynı açıklamayı görüntüler. Bir `Minivan` nesne `car3`olan sonuçları kontrast. Bu durumda, `ShowDetails` `Minivan` sınıfta bildirilen `ShowDetails` `Car` yöntem, sınıfta bildirilen yöntemi geçersiz kılar ve görüntülenen açıklama bir minivan açıklar.  
  
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
  
 `TestCars2`türü `Car`olan nesnelerin bir listesini oluşturur. Nesnelerin değerleri `Car`, ve `ConvertibleCar` `Minivan` sınıflar anlık olarak. `DescribeCar`listenin her öğesine çağrılır. Aşağıdaki kod `TestCars2`.  
  
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
  
 Aşağıdaki çıktı görüntülenir. Tarafından görüntülenen çıktıyla aynı olduğuna dikkat `TestCars1`edin. Sınıfın `ShowDetails` yöntemi, `ConvertibleCar` nesnenin türü , `ConvertibleCar`gibi `TestCars1`, ya da `Car`, . `TestCars2` `car3` Tersine, türü `ShowDetails` veya türü `Minivan` `Minivan` `Car`olup olmadığını, her iki durumda da sınıftan yöntem çağırır.  
  
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
  
 Yöntemleri `TestCars3` `TestCars4` ve örnek tamamlamak. Bu yöntemler `ShowDetails` doğrudan, `ConvertibleCar` ilk olarak türü olduğu `Minivan` `TestCars3`bildirilen nesnelerden ve ( `Car` )`TestCars4`sonra türü olduğu bildirilen nesnelerden ( ) çağırır. Aşağıdaki kod bu iki yöntemi tanımlar.  
  
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
  
 Aşağıdaki kod projenin tamamını ve çıktısını gösterir.  
  
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
- [Sınıflar ve Structs](./index.md)
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [Soyut](../../language-reference/keywords/abstract.md)
