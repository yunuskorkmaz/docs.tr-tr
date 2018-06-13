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
ms.locfileid: "33340274"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="af3f7-102">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="af3f7-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="af3f7-103">C# ' ta türetilmiş bir sınıf yönteminde taban sınıf içinde aynı adı taşıyan bir yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="af3f7-104">Yöntemleri kullanarak nasıl etkileşim belirtebilirsiniz [yeni](../../../csharp/language-reference/keywords/new.md) ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="af3f7-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="af3f7-105">`override` Değiştiricisi *genişletir* temel sınıf yöntemi ve `new` değiştiricisi *gizler* onu.</span><span class="sxs-lookup"><span data-stu-id="af3f7-105">The `override` modifier *extends* the base class method, and the `new` modifier *hides* it.</span></span> <span data-ttu-id="af3f7-106">Bu konudaki örnekler fark gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="af3f7-107">Bir konsol uygulamasında aşağıdaki iki sınıf bildirme `BaseClass` ve `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="af3f7-108">`DerivedClass` öğesinden devralınan `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-109">İçinde `Main` yöntemi, değişkenleri bildirin `bc`, `dc`, ve `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
-   <span data-ttu-id="af3f7-110">`bc` tür `BaseClass`, ve türü değeri olduğu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
-   <span data-ttu-id="af3f7-111">`dc` tür `DerivedClass`, ve türü değeri olduğu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
-   <span data-ttu-id="af3f7-112">`bcdc` tür `BaseClass`, ve türü değeri olduğu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="af3f7-113">Bu dikkat edilmesi gereken değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="af3f7-114">Çünkü `bc` ve `bcdc` türüne sahip `BaseClass`, yalnızca doğrudan erişebilirsiniz `Method1`sürece atama kullanın.</span><span class="sxs-lookup"><span data-stu-id="af3f7-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="af3f7-115">Değişken `dc` her ikisi de erişebilir `Method1` ve `Method2`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="af3f7-116">Bu ilişkileri aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-117">Ardından, aşağıdaki ekleyin `Method2` yöntemine `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="af3f7-118">Bu yöntem imzası imzası eşleşen `Method2` yönteminde `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="af3f7-119">Çünkü `BaseClass` artık bir `Method2` yöntemi, ikinci bir arama ifade eklenebilir için `BaseClass` değişkenleri `bc` ve `bcdc`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="af3f7-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="af3f7-120">Bkz, projeyi derlerken eklenmesi `Method2` yönteminde `BaseClass` bir uyarı neden olur.</span><span class="sxs-lookup"><span data-stu-id="af3f7-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="af3f7-121">Uyarı bildiren `Method2` yönteminde `DerivedClass` gizler `Method2` yönteminde `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="af3f7-122">Kullanmak için önerilir `new` anahtar sözcük `Method2` sonucunda ortaya çıkan neden istiyorsanız tanımı.</span><span class="sxs-lookup"><span data-stu-id="af3f7-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="af3f7-123">Alternatif olarak, aşağıdakilerden birini adlandırabilirsiniz `Method2` uyarı ancak çözmek için yöntemleri değil her zaman pratik.</span><span class="sxs-lookup"><span data-stu-id="af3f7-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="af3f7-124">Eklemeden önce `new`, ek arama deyimleri tarafından üretilen çıkış görmek için programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="af3f7-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="af3f7-125">Aşağıdaki sonuçları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="af3f7-126">`new` Anahtar sözcüğü, bu çıkış üretemeyecek ilişkileri korur, ancak uyarı gizler.</span><span class="sxs-lookup"><span data-stu-id="af3f7-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="af3f7-127">Türüne sahip değişkenler `BaseClass` üyelerini erişmeye devam `BaseClass`, türüne sahip değişkeni `DerivedClass` üyeleri erişmeye devam `DerivedClass` ilk, ardından devralınan üyeler dikkate alınması gereken `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="af3f7-128">Uyarıyı gizlemek için ekleme `new` tanımını değiştiriciyi `Method2` içinde `DerivedClass`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="af3f7-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="af3f7-129">Değiştirici önce veya sonra eklenebilir `public`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="af3f7-130">Çıktı değişmediğini yeniden doğrulamak için programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="af3f7-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="af3f7-131">Ayrıca uyarı artık göründüğünü doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="af3f7-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="af3f7-132">Kullanarak `new`, değiştirdiği üye temel sınıfından devralınan bir üye gizler kullanan çiftidir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="af3f7-133">Devralma yoluyla adı gizleme hakkında daha fazla bilgi için bkz: [new değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="af3f7-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="af3f7-134">Bu davranış kullanmanın etkileri için buna karşılık `override`, aşağıdaki yöntemi ekleyin `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="af3f7-135">`override` Önce veya sonra değiştiricisi eklenebilir `public`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="af3f7-136">Ekleme `virtual` tanımını değiştiriciyi `Method1` içinde `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="af3f7-137">`virtual` Önce veya sonra değiştiricisi eklenebilir `public`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="af3f7-138">Projeyi tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="af3f7-138">Run the project again.</span></span> <span data-ttu-id="af3f7-139">Aşağıdaki çıkış özellikle son iki satırlık dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="af3f7-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="af3f7-140">Kullanımını `override` değiştiricisi etkinleştirir `bcdc` erişimi `Method1` tanımlanan yöntemi `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="af3f7-141">Genellikle, başka bir deyişle istenen davranışı devralma Hiyerarşiler.</span><span class="sxs-lookup"><span data-stu-id="af3f7-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="af3f7-142">Türetilmiş sınıfından türetilen sınıfta tanımlanan yöntemler kullanmayı oluşturulan değerlerine sahip nesneleri istiyor.</span><span class="sxs-lookup"><span data-stu-id="af3f7-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="af3f7-143">Kullanarak bu davranışı elde `override` temel sınıf yöntemi genişletmek için.</span><span class="sxs-lookup"><span data-stu-id="af3f7-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="af3f7-144">Aşağıdaki kod, tam örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-145">Aşağıdaki örnek, farklı bir bağlamda benzer davranış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="af3f7-146">Örnek üç sınıf tanımlar: adlı bir temel sınıf `Car` ve bu sınıftan türetilen iki sınıf `ConvertibleCar` ve `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="af3f7-147">Taban sınıfı içeren bir `DescribeCar` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af3f7-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="af3f7-148">Yöntemi, bir araba temel açıklamasını görüntüler ve çağırır `ShowDetails` ek bilgi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="af3f7-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="af3f7-149">Her üç sınıfların tanımlayan bir `ShowDetails` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af3f7-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="af3f7-150">`new` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `ConvertibleCar` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="af3f7-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="af3f7-151">`override` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `Minivan` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="af3f7-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-152">Örnek hangi sürümünün testleri `ShowDetails` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="af3f7-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="af3f7-153">Aşağıdaki yöntem `TestCars1`her sınıfının bir örneği bildirir ve ardından çağırır `DescribeCar` her örneğindeki.</span><span class="sxs-lookup"><span data-stu-id="af3f7-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-154">`TestCars1` şu çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="af3f7-155">Sonuçları özellikle dikkat edin `car2`, büyük olasılıkla olduğu beklediğinize değil.</span><span class="sxs-lookup"><span data-stu-id="af3f7-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="af3f7-156">Nesne türü `ConvertibleCar`, ancak `DescribeCar` sürümü erişmez `ShowDetails` içinde tanımlanan `ConvertibleCar` bu yöntem ile bildirildiğinden sınıf `new` değiştiricisi, değil `override` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="af3f7-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="af3f7-157">Sonuç olarak, bir `ConvertibleCar` nesne görüntüler aynı açıklama olarak bir `Car` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="af3f7-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="af3f7-158">Sonuçlar için Karşıtlık `car3`, olduğu bir `Minivan` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="af3f7-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="af3f7-159">Bu durumda, `ShowDetails` içinde bildirilen yöntemi `Minivan` geçersiz kılmaları sınıf `ShowDetails` içinde bildirilen yöntemi `Car` sınıfı ve görüntülenen açıklama bir minivan açıklar.</span><span class="sxs-lookup"><span data-stu-id="af3f7-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-160">`TestCars2` türüne sahip nesnelerin bir listesini oluşturur `Car`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="af3f7-161">Değerlerin nesnelerin örneği oluşturulmadan `Car`, `ConvertibleCar`, ve `Minivan` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="af3f7-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="af3f7-162">`DescribeCar` Listenin her öğesinin adı verilir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="af3f7-163">Aşağıdaki kod tanımını gösterir `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-164">Aşağıdaki çıktısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-164">The following output is displayed.</span></span> <span data-ttu-id="af3f7-165">Tarafından görüntülenen çıktı ile aynı olduğunu fark `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="af3f7-166">`ShowDetails` Yöntemi `ConvertibleCar` sınıfı çağrılmaz, nesne türü olmasına bakılmaksızın `ConvertibleCar`, olarak `TestCars1`, veya `Car`, olarak `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="af3f7-167">Buna karşılık, `car3` çağrıları `ShowDetails` yönteminden `Minivan` türüne sahip olup olmadığını her iki durumda da sınıf `Minivan` veya türü `Car`.</span><span class="sxs-lookup"><span data-stu-id="af3f7-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-168">Yöntemleri `TestCars3` ve `TestCars4` tam örnek.</span><span class="sxs-lookup"><span data-stu-id="af3f7-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="af3f7-169">Bu yöntemleri `ShowDetails` doğrudan ilk nesnelerden bildirilen türün `ConvertibleCar` ve `Minivan` (`TestCars3`), ardından türün bildirilen nesnelerinden `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="af3f7-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="af3f7-170">Aşağıdaki kod bu iki yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af3f7-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-171">Yöntemleri, bu konunun ilk örneğindeki sonuçları karşılık gelen aşağıdaki çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="af3f7-172">Aşağıdaki kod, tam projeyi ve çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af3f7-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af3f7-173">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af3f7-173">See Also</span></span>  
 [<span data-ttu-id="af3f7-174">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="af3f7-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="af3f7-175">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="af3f7-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="af3f7-176">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="af3f7-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="af3f7-177">base</span><span class="sxs-lookup"><span data-stu-id="af3f7-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="af3f7-178">abstract</span><span class="sxs-lookup"><span data-stu-id="af3f7-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)
