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
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="d2f25-103">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d2f25-103">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="d2f25-104">C# ' de, türetilmiş sınıftaki bir yöntem, temel sınıftaki bir yöntemle aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-104">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="d2f25-105">Yöntemlerinin [New](../../language-reference/keywords/new-modifier.md) ve [override](../../language-reference/keywords/override.md) anahtar sözcüklerini kullanarak nasıl etkileşime gireceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2f25-105">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="d2f25-106">`override`Değiştirici, *extends* temel sınıf yöntemini genişletir `virtual` ve `new` değiştirici, erişilebilir bir temel sınıf yöntemini *gizler* .</span><span class="sxs-lookup"><span data-stu-id="d2f25-106">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="d2f25-107">Fark, bu konudaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-107">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="d2f25-108">Konsol uygulamasında, aşağıdaki iki sınıfı bildirin `BaseClass` ve `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-108">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="d2f25-109">`DerivedClass`öğesinden devralır `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-109">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-110">Yönteminde, `Main` ve değişkenlerini bildirin `bc` `dc` `bcdc` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-110">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="d2f25-111">`bc`türündedir `BaseClass` ve değeri türündedir `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-111">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="d2f25-112">`dc`türündedir `DerivedClass` ve değeri türündedir `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-112">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="d2f25-113">`bcdc`türündedir `BaseClass` ve değeri türündedir `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-113">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="d2f25-114">Bu, dikkat edilmesi gereken değişkendir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-114">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="d2f25-115">`bc`Ve `bcdc` türü olduğundan `BaseClass` , atama kullanmadığınız müddetçe yalnızca doğrudan erişim sağlayabilir `Method1` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-115">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="d2f25-116">Değişken, `dc` `Method1` ve ' a erişebilir `Method2` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-116">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="d2f25-117">Bu ilişkiler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-117">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-118">Ardından, aşağıdaki `Method2` yöntemi öğesine ekleyin `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-118">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="d2f25-119">Bu yöntemin imzası `Method2` içindeki yönteminin imzasıyla eşleşir `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-119">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="d2f25-120">`BaseClass`Artık bir yöntemi olduğundan `Method2` , `BaseClass` `bc` `bcdc` aşağıdaki kodda gösterildiği gibi, değişkenler için ikinci bir çağırma açıklaması eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-120">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="d2f25-121">Projeyi derlediğinizde, `Method2` içinde yönteminin eklenmesi `BaseClass` bir uyarıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="d2f25-121">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="d2f25-122">Uyarı, `Method2` içindeki yönteminin `DerivedClass` içindeki yöntemi gizlediğini belirtir `Method2` `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-122">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="d2f25-123">`new`Bu sonuca neden olmak istiyorsanız, tanımda anahtar sözcüğünü kullanmanız önerilir `Method2` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-123">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="d2f25-124">Alternatif olarak, `Method2` uyarıyı çözümlemek için yöntemlerden birini yeniden adlandırabilirsiniz, ancak her zaman pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-124">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="d2f25-125">Eklemeden önce `new` , ek çağırma deyimleri tarafından üretilen çıktıyı görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2f25-125">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="d2f25-126">Aşağıdaki sonuçlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-126">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="d2f25-127">`new`Anahtar sözcüğü, bu çıktıyı üreten ilişkileri korur, ancak uyarıyı bastırır.</span><span class="sxs-lookup"><span data-stu-id="d2f25-127">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="d2f25-128">Türüne sahip değişkenler `BaseClass` , üyelerine erişmeye devam `BaseClass` eder ve türüne sahip olan değişken `DerivedClass` ilk olarak üyelere erişmeye devam eder `DerivedClass` ve öğesinden devralınan üyeleri göz önünde bulundurun `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-128">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="d2f25-129">Uyarıyı bastırmak için, `new` `Method2` `DerivedClass` aşağıdaki kodda gösterildiği gibi değiştiricisini içindeki tanımına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2f25-129">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="d2f25-130">Değiştirici veya daha önce eklenebilir `public` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-130">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="d2f25-131">Çıktının değiştirilmediğini doğrulamak için programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2f25-131">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="d2f25-132">Ayrıca uyarının artık göründüğünü doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d2f25-132">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="d2f25-133">Kullanarak `new` , değiştirdiği üyenin, temel sınıftan devralınan bir üyeyi gizlediğini fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="d2f25-133">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="d2f25-134">Devralma yoluyla ad gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="d2f25-134">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="d2f25-135">Bu davranışı kullanmanın etkilerine karşı tersine geçmek için `override` aşağıdaki yöntemi öğesine ekleyin `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-135">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="d2f25-136">`override`Değiştirici veya daha önce eklenebilir `public` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-136">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="d2f25-137">`virtual`Değiştiricisini içindeki tanımına ekleyin `Method1` `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-137">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="d2f25-138">`virtual`Değiştirici veya daha önce eklenebilir `public` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-138">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="d2f25-139">Projeyi tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2f25-139">Run the project again.</span></span> <span data-ttu-id="d2f25-140">Özellikle aşağıdaki Çıktının son iki satırını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d2f25-140">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="d2f25-141">Değiştiricinin kullanımı, `override` `bcdc` `Method1` içinde tanımlanan yönteme erişim sağlar `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-141">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="d2f25-142">Genellikle, devralma hiyerarşilerindeki istenen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="d2f25-142">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="d2f25-143">Türetilmiş sınıftan oluşturulan değerlere sahip nesnelerin türetilmiş sınıfta tanımlanan yöntemleri kullanmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d2f25-143">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="d2f25-144">`override`Temel sınıf yöntemini genişletmek için bu davranışı kullanarak elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="d2f25-144">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="d2f25-145">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-145">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-146">Aşağıdaki örnek farklı bağlamdaki benzer davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-146">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="d2f25-147">Örnek üç sınıfı tanımlar: adlı bir temel sınıf `Car` ve ondan türetilmiş iki sınıf `ConvertibleCar` ve `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-147">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="d2f25-148">Temel sınıf bir yöntemi içerir `DescribeCar` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-148">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="d2f25-149">Yöntemi, bir araba için temel bir açıklama görüntüler ve daha sonra `ShowDetails` ek bilgi sağlamak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="d2f25-149">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="d2f25-150">Üç sınıfın her biri bir yöntemi tanımlar `ShowDetails` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-150">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="d2f25-151">`new`Değiştirici sınıfında tanımlamak için kullanılır `ShowDetails` `ConvertibleCar` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-151">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="d2f25-152">`override`Değiştirici sınıfında tanımlamak için kullanılır `ShowDetails` `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-152">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-153">Örnek, hangi sürümünün çağrıldığını sınar `ShowDetails` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-153">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="d2f25-154">Aşağıdaki yöntem, `TestCars1` her sınıfın bir örneğini bildirir ve ardından `DescribeCar` her bir örnek üzerinde çağırır.</span><span class="sxs-lookup"><span data-stu-id="d2f25-154">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-155">`TestCars1`Aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-155">`TestCars1` produces the following output.</span></span> <span data-ttu-id="d2f25-156">Özellikle `car2` , beklendikleriniz olmayan büyük olasılıkla için sonuçları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2f25-156">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="d2f25-157">Nesnenin türü, `ConvertibleCar` ancak `DescribeCar` `ShowDetails` `ConvertibleCar` Bu yöntem değiştirici `new` değil değiştiriciyle bildirildiği için sınıfında tanımlanan sürümüne erişmez `override` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-157">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="d2f25-158">Sonuç olarak, bir `ConvertibleCar` nesnesi bir nesneyle aynı açıklamayı görüntüler `Car` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-158">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="d2f25-159">`car3`Bir nesnesi olan için sonuçlarını kontrast `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-159">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="d2f25-160">Bu durumda, `ShowDetails` sınıfında belirtilen yöntem, `Minivan` `ShowDetails` sınıfında belirtilen yöntemi geçersiz kılar `Car` ve görüntülenen açıklama bir mini Van 'yi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2f25-160">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-161">`TestCars2`türü olan nesnelerin bir listesini oluşturur `Car` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-161">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="d2f25-162">Nesnelerin değerleri `Car` ,, `ConvertibleCar` ve `Minivan` sınıflarından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d2f25-162">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="d2f25-163">`DescribeCar`, listedeki her öğe için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d2f25-163">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="d2f25-164">Aşağıdaki kod tanımını gösterir `TestCars2` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-164">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-165">Aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-165">The following output is displayed.</span></span> <span data-ttu-id="d2f25-166">Bunun, tarafından görüntülenen çıktıyla aynı olduğuna dikkat edin `TestCars1` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-166">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="d2f25-167">Sınıfının yöntemi, nesne türünün ' de olduğu gibi, veya ' de olduğu gibi `ShowDetails` `ConvertibleCar` çağrılmaz `ConvertibleCar` `TestCars1` `Car` `TestCars2` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-167">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="d2f25-168">Buna karşılık, `car3` `ShowDetails` `Minivan` tür veya tür içerip içermediğini her iki durumda da sınıfından yöntemini çağırır `Minivan` `Car` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-168">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-169">Yöntemini `TestCars3` `TestCars4` doldurun ve örnek.</span><span class="sxs-lookup"><span data-stu-id="d2f25-169">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="d2f25-170">Bu yöntemler `ShowDetails` , önce türü ve () olan olarak belirtilen nesnelerden `ConvertibleCar` `Minivan` `TestCars3` , daha sonra türü () olan olarak belirtilen nesnelerden doğrudan `Car` çağrı yapılır `TestCars4` .</span><span class="sxs-lookup"><span data-stu-id="d2f25-170">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="d2f25-171">Aşağıdaki kod bu iki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2f25-171">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-172">Yöntemler, bu konudaki ilk örnekteki sonuçlara karşılık gelen aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-172">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="d2f25-173">Aşağıdaki kod, tüm projeyi ve çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2f25-173">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2f25-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2f25-174">See also</span></span>

- [<span data-ttu-id="d2f25-175">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d2f25-175">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d2f25-176">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="d2f25-176">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d2f25-177">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2f25-177">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="d2f25-178">base</span><span class="sxs-lookup"><span data-stu-id="d2f25-178">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="d2f25-179">Soyut</span><span class="sxs-lookup"><span data-stu-id="d2f25-179">abstract</span></span>](../../language-reference/keywords/abstract.md)
