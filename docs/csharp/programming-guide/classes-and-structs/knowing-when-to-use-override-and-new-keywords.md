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
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="e7310-102">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e7310-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="e7310-103">İçinde C#, türetilmiş bir sınıftaki bir yöntem, temel sınıftaki bir yöntemle aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7310-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="e7310-104">Yöntemlerinin [New](../../language-reference/keywords/new-modifier.md) ve [override](../../language-reference/keywords/override.md) anahtar sözcüklerini kullanarak nasıl etkileşime gireceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7310-104">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="e7310-105">`virtual` `new` Değiştirici, temel sınıf yöntemini genişletir ve değiştirici, erişilebilir bir temel sınıf yöntemini gizler. `override`</span><span class="sxs-lookup"><span data-stu-id="e7310-105">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="e7310-106">Fark, bu konudaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7310-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="e7310-107">Konsol uygulamasında, aşağıdaki iki sınıfı `BaseClass` bildirin ve. `DerivedClass`</span><span class="sxs-lookup"><span data-stu-id="e7310-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="e7310-108">`DerivedClass`öğesinden `BaseClass`devralır.</span><span class="sxs-lookup"><span data-stu-id="e7310-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="e7310-109">Yönteminde, ve `bc` değişkenlerinibildirin.`bcdc` `dc` `Main`</span><span class="sxs-lookup"><span data-stu-id="e7310-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="e7310-110">`bc`türündedir `BaseClass`ve değeri türündedir `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="e7310-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="e7310-111">`dc`türündedir `DerivedClass`ve değeri türündedir `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="e7310-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="e7310-112">`bcdc`türündedir `BaseClass`ve değeri türündedir `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="e7310-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="e7310-113">Bu, dikkat edilmesi gereken değişkendir.</span><span class="sxs-lookup"><span data-stu-id="e7310-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="e7310-114">Ve `bc` türüolduğundan`BaseClass`, atama kullanmadığınız müddetçe yalnızca doğrudan erişim `Method1`sağlayabilir. `bcdc`</span><span class="sxs-lookup"><span data-stu-id="e7310-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="e7310-115">Değişken `dc` , `Method1` ve ' `Method2`a erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e7310-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="e7310-116">Bu ilişkiler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7310-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="e7310-117">Ardından, aşağıdaki `Method2` yöntemi öğesine `BaseClass`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7310-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="e7310-118">Bu yöntemin imzası içindeki `Method2` `DerivedClass`yönteminin imzasıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e7310-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="e7310-119">Artık `BaseClass` bir `BaseClass` `bc` `bcdc`yöntemi olduğundan, aşağıdaki kodda gösterildiği gibi, değişkenler için ikinci bir çağırma açıklaması eklenebilir. `Method2`</span><span class="sxs-lookup"><span data-stu-id="e7310-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="e7310-120">Projeyi derlediğinizde, içinde `Method2` `BaseClass` yönteminin eklenmesi bir uyarıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="e7310-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="e7310-121">Uyarı, içindeki `DerivedClass` yönteminin içindeki `Method2` `Method2` yöntemigizlediğinibelirtir`BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="e7310-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="e7310-122">Bu sonuca neden olmak istiyorsanız, `new` `Method2` tanımda anahtar sözcüğünü kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="e7310-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="e7310-123">Alternatif olarak, uyarıyı çözümlemek için `Method2` yöntemlerden birini yeniden adlandırabilirsiniz, ancak her zaman pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="e7310-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="e7310-124">Eklemeden `new`önce, ek çağırma deyimleri tarafından üretilen çıktıyı görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e7310-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="e7310-125">Aşağıdaki sonuçlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e7310-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="e7310-126">`new` Anahtar sözcüğü, bu çıktıyı üreten ilişkileri korur, ancak uyarıyı bastırır.</span><span class="sxs-lookup"><span data-stu-id="e7310-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="e7310-127">Türüne `BaseClass` sahip değişkenler `BaseClass`, üyelerine erişmeye devam eder ve türüne `DerivedClass` sahip olan değişken ilk olarak `DerivedClass` üyelere erişmeye devam eder ve öğesinden `BaseClass`devralınan üyeleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e7310-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="e7310-128">Uyarıyı bastırmak için, aşağıdaki kodda gösterildiği `new` gibi değiştiricisini `Method2` içindeki `DerivedClass`tanımına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7310-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="e7310-129">Değiştirici veya `public`daha önce eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e7310-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="e7310-130">Çıktının değiştirilmediğini doğrulamak için programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e7310-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="e7310-131">Ayrıca uyarının artık göründüğünü doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e7310-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="e7310-132">Kullanarak `new`, değiştirdiği üyenin, temel sınıftan devralınan bir üyeyi gizlediğini fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="e7310-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="e7310-133">Devralma yoluyla ad gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="e7310-133">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="e7310-134">Bu davranışı kullanmanın `override`etkilerine karşı tersine geçmek için aşağıdaki yöntemi öğesine `DerivedClass`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7310-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="e7310-135">Değiştirici veya daha önce eklenebilir. `public` `override`</span><span class="sxs-lookup"><span data-stu-id="e7310-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="e7310-136">`virtual` Değiştiricisini`Method1` içindeki tanımına`BaseClass`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7310-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="e7310-137">Değiştirici veya daha önce eklenebilir. `public` `virtual`</span><span class="sxs-lookup"><span data-stu-id="e7310-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="e7310-138">Projeyi yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e7310-138">Run the project again.</span></span> <span data-ttu-id="e7310-139">Özellikle aşağıdaki Çıktının son iki satırını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e7310-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="e7310-140">`override` Değiştiricinin kullanımı, içinde `bcdc` `Method1` tanımlanan`DerivedClass`yönteme erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7310-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="e7310-141">Genellikle, devralma hiyerarşilerindeki istenen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="e7310-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="e7310-142">Türetilmiş sınıftan oluşturulan değerlere sahip nesnelerin türetilmiş sınıfta tanımlanan yöntemleri kullanmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e7310-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="e7310-143">Temel sınıf yöntemini genişletmek için bu `override` davranışı kullanarak elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="e7310-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="e7310-144">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="e7310-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="e7310-145">Aşağıdaki örnek farklı bağlamdaki benzer davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7310-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="e7310-146">Örnek üç sınıfı tanımlar: adlı `Car` bir temel sınıf ve ondan türetilmiş `ConvertibleCar` iki sınıf ve `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="e7310-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="e7310-147">Temel sınıf bir `DescribeCar` yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="e7310-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="e7310-148">Yöntemi, bir araba için temel bir açıklama görüntüler ve daha sonra ek `ShowDetails` bilgi sağlamak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="e7310-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="e7310-149">Üç sınıfın her biri bir `ShowDetails` yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7310-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="e7310-150">Değiştirici sınıfında tanımlamak `ShowDetails` için kullanılır. `ConvertibleCar` `new`</span><span class="sxs-lookup"><span data-stu-id="e7310-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="e7310-151">Değiştirici sınıfında tanımlamak `ShowDetails` için kullanılır. `Minivan` `override`</span><span class="sxs-lookup"><span data-stu-id="e7310-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="e7310-152">Örnek, hangi sürümünün `ShowDetails` çağrıldığını sınar.</span><span class="sxs-lookup"><span data-stu-id="e7310-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="e7310-153">Aşağıdaki yöntem `TestCars1`, her sınıfın bir örneğini bildirir ve ardından her bir örnek üzerinde çağırır `DescribeCar` .</span><span class="sxs-lookup"><span data-stu-id="e7310-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="e7310-154">`TestCars1`Aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="e7310-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="e7310-155">Özellikle, beklendikleriniz `car2`olmayan büyük olasılıkla için sonuçları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7310-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="e7310-156">`ConvertibleCar`Nesnenin `new` türü, `DescribeCar` ancak bu yöntem değiştirici değil `ShowDetails` `ConvertibleCar` değiştiriciylebildirildiğiiçinsınıfındatanımlanan`override` sürümüne erişmez.</span><span class="sxs-lookup"><span data-stu-id="e7310-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="e7310-157">Sonuç olarak, `ConvertibleCar` bir nesnesi bir `Car` nesneyle aynı açıklamayı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e7310-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="e7310-158">`car3` Bir`Minivan` nesnesi olan için sonuçlarını kontrast.</span><span class="sxs-lookup"><span data-stu-id="e7310-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="e7310-159">Bu `ShowDetails` durumda, `Minivan` sınıfında belirtilen yöntem, `Car` sınıfında belirtilen `ShowDetails` yöntemi geçersiz kılar ve görüntülenen açıklama bir mini Van 'yi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7310-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="e7310-160">`TestCars2`türü `Car`olan nesnelerin bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e7310-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="e7310-161">Nesnelerin değerleri `Car`, `ConvertibleCar`, ve `Minivan` sınıflarından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e7310-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="e7310-162">`DescribeCar`, listedeki her öğe için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e7310-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="e7310-163">Aşağıdaki kod tanımını `TestCars2`gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7310-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="e7310-164">Aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e7310-164">The following output is displayed.</span></span> <span data-ttu-id="e7310-165">Bunun, tarafından `TestCars1`görüntülenen çıktıyla aynı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e7310-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="e7310-166">`ShowDetails` `Car`Sınıfının yöntemi `TestCars2`, nesne `ConvertibleCar`türünün ' de olduğu gibi, veya ' de olduğu gibi çağrılmaz. `TestCars1` `ConvertibleCar`</span><span class="sxs-lookup"><span data-stu-id="e7310-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="e7310-167">Buna karşılık `car3` , tür `ShowDetails` `Minivan` veyatür`Car`içerip içermediğini her iki durumda da sınıfından yöntemini çağırır. `Minivan`</span><span class="sxs-lookup"><span data-stu-id="e7310-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="e7310-168">Yöntemini `TestCars3` doldurun `TestCars4` ve örnek.</span><span class="sxs-lookup"><span data-stu-id="e7310-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="e7310-169">Bu yöntemler, `ShowDetails` önce türü `ConvertibleCar` ve `Minivan` (`TestCars3`) olan olarak belirtilen nesnelerden, daha sonra türü `Car` (`TestCars4`) olan olarak belirtilen nesnelerden doğrudan çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="e7310-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="e7310-170">Aşağıdaki kod bu iki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7310-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="e7310-171">Yöntemler, bu konudaki ilk örnekteki sonuçlara karşılık gelen aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="e7310-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="e7310-172">Aşağıdaki kod, tüm projeyi ve çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7310-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7310-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7310-173">See also</span></span>

- [<span data-ttu-id="e7310-174">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e7310-174">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e7310-175">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="e7310-175">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e7310-176">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7310-176">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="e7310-177">base</span><span class="sxs-lookup"><span data-stu-id="e7310-177">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="e7310-178">abstract</span><span class="sxs-lookup"><span data-stu-id="e7310-178">abstract</span></span>](../../language-reference/keywords/abstract.md)
