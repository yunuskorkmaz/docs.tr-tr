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
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="f4be4-102">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f4be4-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="f4be4-103">İçinde C#, türetilmiş bir sınıftaki bir yöntem, temel sınıftaki bir yöntemle aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="f4be4-104">Yöntemlerinin [New](../../language-reference/keywords/new-modifier.md) ve [override](../../language-reference/keywords/override.md) anahtar sözcüklerini kullanarak nasıl etkileşime gireceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4be4-104">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="f4be4-105">`override` değiştirici temel sınıf `virtual` yöntemini *genişletir* ve `new` değiştiricisi erişilebilir bir temel sınıf yöntemini *gizler* .</span><span class="sxs-lookup"><span data-stu-id="f4be4-105">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="f4be4-106">Fark, bu konudaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="f4be4-107">Konsol uygulamasında, `BaseClass` ve `DerivedClass`aşağıdaki iki sınıfı bildirin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="f4be4-108">`DerivedClass` `BaseClass`devralır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-109">`Main` yönteminde, değişkenleri `bc`, `dc`ve `bcdc`bildirin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="f4be4-110">`bc` `BaseClass`türüdür ve değeri `BaseClass`türündedir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="f4be4-111">`dc` `DerivedClass`türüdür ve değeri `DerivedClass`türündedir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="f4be4-112">`bcdc` `BaseClass`türüdür ve değeri `DerivedClass`türündedir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="f4be4-113">Bu, dikkat edilmesi gereken değişkendir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="f4be4-114">`bc` ve `bcdc` tür `BaseClass`olduğundan, atama kullanmadığınız müddetçe yalnızca `Method1`doğrudan erişim sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="f4be4-115">Değişken `dc`, hem `Method1` hem de `Method2`erişebilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="f4be4-116">Bu ilişkiler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-117">Sonra, `BaseClass`için aşağıdaki `Method2` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="f4be4-118">Bu yöntemin imzası, `DerivedClass``Method2` yönteminin imzasıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="f4be4-119">`BaseClass` artık `Method2` bir yöntemi olduğundan, aşağıdaki kodda gösterildiği gibi `BaseClass` değişkenleri `bc` ve `bcdc`için ikinci bir çağrı ekstresi eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="f4be4-120">Projeyi derlediğinizde `Method2` yönteminin `BaseClass` bir uyarıya neden olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f4be4-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="f4be4-121">Uyarı, `DerivedClass` `Method2` yönteminin `BaseClass``Method2` yöntemini gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="f4be4-122">Bu sonuca neden olmak istiyorsanız `Method2` tanımında `new` anahtar sözcüğünü kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="f4be4-123">Alternatif olarak, uyarıyı çözümlemek için `Method2` yöntemlerinden birini yeniden adlandırabilirsiniz, ancak bu her zaman pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="f4be4-124">`new`eklemeden önce, ek çağırma deyimleri tarafından üretilen çıktıyı görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f4be4-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="f4be4-125">Aşağıdaki sonuçlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="f4be4-126">`new` anahtar sözcüğü, bu çıktıyı üreten ilişkileri korur, ancak uyarıyı bastırır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="f4be4-127">Türü `BaseClass` olan değişkenler `BaseClass`üyelerine erişmeye devam eder ve tür `DerivedClass` olan değişken, önce `DerivedClass` üyelere erişmeye devam eder ve ardından `BaseClass`devralınmış üyeleri göz önüne alın.</span><span class="sxs-lookup"><span data-stu-id="f4be4-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="f4be4-128">Uyarıyı bastırmak için, aşağıdaki kodda gösterildiği gibi `new` değiştiricisini `DerivedClass``Method2` tanımına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="f4be4-129">Değiştirici, `public`önce veya sonra eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="f4be4-130">Çıktının değiştirilmediğini doğrulamak için programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f4be4-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="f4be4-131">Ayrıca uyarının artık göründüğünü doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f4be4-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="f4be4-132">`new`kullanarak, değiştirdiği üyenin, temel sınıftan devralınan bir üyeyi gizlediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f4be4-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="f4be4-133">Devralma yoluyla ad gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="f4be4-133">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="f4be4-134">Bu davranışı `override`kullanmanın etkilerinin aksine, `DerivedClass`için aşağıdaki yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="f4be4-135">`override` değiştiricisi `public`önce veya sonra eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="f4be4-136">`virtual` değiştiricisini `BaseClass``Method1` tanımına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="f4be4-137">`virtual` değiştiricisi `public`önce veya sonra eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="f4be4-138">Projeyi tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f4be4-138">Run the project again.</span></span> <span data-ttu-id="f4be4-139">Özellikle aşağıdaki Çıktının son iki satırını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f4be4-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="f4be4-140">`override` değiştiricisinin kullanımı, `bcdc` `DerivedClass`tanımlanmış `Method1` yöntemine erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4be4-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="f4be4-141">Genellikle, devralma hiyerarşilerindeki istenen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="f4be4-142">Türetilmiş sınıftan oluşturulan değerlere sahip nesnelerin türetilmiş sınıfta tanımlanan yöntemleri kullanmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f4be4-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="f4be4-143">Temel sınıf yöntemini genişletmek için `override` kullanarak bu davranışı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="f4be4-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="f4be4-144">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-145">Aşağıdaki örnek farklı bağlamdaki benzer davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="f4be4-146">Örnek üç sınıfı tanımlar: `Car` adlı bir temel sınıf ve bundan türetilmiş iki sınıf, `ConvertibleCar` ve `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="f4be4-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="f4be4-147">Temel sınıf bir `DescribeCar` yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="f4be4-148">Yöntemi, bir araba için temel bir açıklama görüntüler ve daha sonra ek bilgi sağlamak için `ShowDetails` çağırır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="f4be4-149">Üç sınıfın her biri bir `ShowDetails` yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4be4-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="f4be4-150">`new` değiştiricisi `ConvertibleCar` sınıfında `ShowDetails` tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="f4be4-151">`override` değiştiricisi `Minivan` sınıfında `ShowDetails` tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-152">Örnek, hangi `ShowDetails` sürümünün çağrıldığını sınar.</span><span class="sxs-lookup"><span data-stu-id="f4be4-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="f4be4-153">Aşağıdaki yöntem `TestCars1`, her sınıfın bir örneğini bildirir ve sonra her bir örnekteki `DescribeCar` çağırır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-154">`TestCars1` aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="f4be4-155">Büyük olasılıkla beklendikleriniz olmayan `car2`için sonuçlara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="f4be4-156">Nesnenin türü `ConvertibleCar`, ancak bu yöntem `new` değiştiricisiyle değil `override` değiştiriciyle bildirildiği için, `DescribeCar` `ConvertibleCar` sınıfında tanımlanan `ShowDetails` sürümüne erişemez.</span><span class="sxs-lookup"><span data-stu-id="f4be4-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="f4be4-157">Sonuç olarak, bir `ConvertibleCar` nesnesi aynı açıklamayı bir `Car` nesnesi ile görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f4be4-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="f4be4-158">Bir `Minivan` nesnesi olan `car3`için sonuçları kontrast.</span><span class="sxs-lookup"><span data-stu-id="f4be4-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="f4be4-159">Bu durumda, `Minivan` sınıfında belirtilen `ShowDetails` yöntemi `Car` sınıfında belirtilen `ShowDetails` yöntemini geçersiz kılar ve görüntülenen açıklama bir mini Van 'yi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4be4-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-160">`TestCars2`, `Car`türüne sahip nesnelerin bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4be4-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="f4be4-161">Nesnelerin değerleri `Car`, `ConvertibleCar`ve `Minivan` sınıflarından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f4be4-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="f4be4-162">`DescribeCar`, listedeki her öğe için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f4be4-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="f4be4-163">Aşağıdaki kod `TestCars2`tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-164">Aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-164">The following output is displayed.</span></span> <span data-ttu-id="f4be4-165">`TestCars1`tarafından görüntülenen çıktıyla aynı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f4be4-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="f4be4-166">`ConvertibleCar` sınıfının `ShowDetails` yöntemi, nesnenin türünün `TestCars1`veya `Car`gibi `TestCars2`gibi `ConvertibleCar`olmasına bakılmaksızın çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="f4be4-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="f4be4-167">Buna karşılık `car3`, `ShowDetails` yöntemini her iki durumda da `Minivan` sınıfından çağırır `Minivan` veya `Car`yazın.</span><span class="sxs-lookup"><span data-stu-id="f4be4-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-168">Yöntemler `TestCars3` ve `TestCars4` örneğini tamamlar.</span><span class="sxs-lookup"><span data-stu-id="f4be4-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="f4be4-169">Bu yöntemler, öncelikle tür `ConvertibleCar` ve `Minivan` (`TestCars3`) sahip olduğu belirtilen nesnelerden, daha sonra tür `Car` (`TestCars4`) sahip olarak belirtilen nesnelerden `ShowDetails`.</span><span class="sxs-lookup"><span data-stu-id="f4be4-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="f4be4-170">Aşağıdaki kod bu iki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4be4-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-171">Yöntemler, bu konudaki ilk örnekteki sonuçlara karşılık gelen aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="f4be4-172">Aşağıdaki kod, tüm projeyi ve çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4be4-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4be4-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4be4-173">See also</span></span>

- [<span data-ttu-id="f4be4-174">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f4be4-174">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f4be4-175">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="f4be4-175">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="f4be4-176">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4be4-176">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="f4be4-177">base</span><span class="sxs-lookup"><span data-stu-id="f4be4-177">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="f4be4-178">abstract</span><span class="sxs-lookup"><span data-stu-id="f4be4-178">abstract</span></span>](../../language-reference/keywords/abstract.md)
