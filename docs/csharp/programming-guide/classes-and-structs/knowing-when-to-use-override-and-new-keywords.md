---
title: Geçersiz kılma ve yeni anahtar sözcüklerle - ne zaman kullanılacağını bilme C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: eae57ae1f285e7f0e44c49e3d54fbd81bb4be591
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398435"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="95b81-102">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="95b81-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="95b81-103">C# ' ta türetilen bir sınıfta bir yöntem temel sınıfta bir yöntem adıyla aynı olabilir.</span><span class="sxs-lookup"><span data-stu-id="95b81-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="95b81-104">Yöntemleri kullanarak etkileşimini belirtebilirsiniz [yeni](../../../csharp/language-reference/keywords/new-modifier.md) ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="95b81-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new-modifier.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="95b81-105">`override` Değiştiricisi *genişletir* temel sınıf `virtual` yöntemi ve `new` değiştiricisi *gizler* erişilebilir temel sınıf yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b81-105">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="95b81-106">Fark, bu konudaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="95b81-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="95b81-107">Bir konsol uygulamasında aşağıdaki iki sınıf bildirme `BaseClass` ve `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="95b81-108">`DerivedClass` devralınan `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="95b81-109">İçinde `Main` yöntemi, değişkenleri `bc`, `dc`, ve `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="95b81-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="95b81-110">`bc` tür `BaseClass`, ve değeri türü `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="95b81-111">`dc` tür `DerivedClass`, ve değeri türü `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="95b81-112">`bcdc` tür `BaseClass`, ve değeri türü `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="95b81-113">Değişken dikkat edilmesi gereken budur.</span><span class="sxs-lookup"><span data-stu-id="95b81-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="95b81-114">Çünkü `bc` ve `bcdc` türüne sahip `BaseClass`, yalnızca doğrudan erişebilir `Method1`atama kullandığınız sürece.</span><span class="sxs-lookup"><span data-stu-id="95b81-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="95b81-115">Değişken `dc` hem erişim `Method1` ve `Method2`.</span><span class="sxs-lookup"><span data-stu-id="95b81-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="95b81-116">Bu ilişkiler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="95b81-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="95b81-117">Ardından, aşağıdaki ekleyin `Method2` yönteme `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="95b81-118">Bu yöntemin imzası imzası eşleşen `Method2` yönteminde `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="95b81-119">Çünkü `BaseClass` artık bir `Method2` yönteminde deyim çağırma ikinci eklenebilir için `BaseClass` değişkenleri `bc` ve `bcdc`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="95b81-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="95b81-120">Proje oluşturduğunuzda, gördüğünüz eklenmesini `Method2` yöntemi `BaseClass` bir uyarısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="95b81-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="95b81-121">Uyarı bildiren `Method2` yönteminde `DerivedClass` gizler `Method2` yönteminde `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="95b81-122">Kullanılacak kopyaladınız `new` anahtar sözcüğünü `Method2` sonucunda ortaya çıkan neden istiyorsanız, tanım.</span><span class="sxs-lookup"><span data-stu-id="95b81-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="95b81-123">Alternatif olarak, aşağıdakilerden birini adlandırabilirsiniz `Method2` uyarı ancak çözmek için yöntemleri değil her zaman pratik.</span><span class="sxs-lookup"><span data-stu-id="95b81-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="95b81-124">Eklemeden önce `new`, ek çağrıyı yapan ifadeler tarafından üretilen çıktıyı görmek için programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="95b81-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="95b81-125">Aşağıdaki sonuçları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="95b81-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="95b81-126">`new` Anahtar sözcüğü bu çıkışı üreten ilişkileri korur, ancak uyarı bastırır.</span><span class="sxs-lookup"><span data-stu-id="95b81-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="95b81-127">Türüne sahip değişkenler `BaseClass` üyelerinin erişmeye devam `BaseClass`ve türünde değişken `DerivedClass` üyeleri erişmeye devam `DerivedClass` ilk olarak ve ardından öğesinden devralınan üyelere dikkate alınması gereken `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="95b81-128">Uyarıyı bastırmak için ekleme `new` tanımının değiştiricisi `Method2` içinde `DerivedClass`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="95b81-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="95b81-129">Önce veya sonra değiştiricisi eklenebilir `public`.</span><span class="sxs-lookup"><span data-stu-id="95b81-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="95b81-130">Çıkış değiştirilmedi yeniden doğrulamak için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="95b81-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="95b81-131">Ayrıca uyarı artık göründüğünü doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="95b81-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="95b81-132">Kullanarak `new`, değiştirdiği üyesi temel sınıftan devralınan üyeyi gizler haberdar olduğunuzu çiftidir.</span><span class="sxs-lookup"><span data-stu-id="95b81-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="95b81-133">Devralma üzerinden ad gizleme hakkında daha fazla bilgi için bkz: [new değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="95b81-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="95b81-134">Bu davranış kullanmanın etkileri için buna karşılık `override`, aşağıdaki yöntemi ekleyin `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="95b81-135">`override` Değiştiricisi eklenebilir, önce veya sonra `public`.</span><span class="sxs-lookup"><span data-stu-id="95b81-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="95b81-136">Ekleme `virtual` tanımının değiştiricisi `Method1` içinde `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="95b81-137">`virtual` Değiştiricisi eklenebilir, önce veya sonra `public`.</span><span class="sxs-lookup"><span data-stu-id="95b81-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="95b81-138">Projeyi yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="95b81-138">Run the project again.</span></span> <span data-ttu-id="95b81-139">Aşağıdaki çıktı özellikle son iki satırlık dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="95b81-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="95b81-140">Kullanımını `override` değiştirici etkinleştirir `bcdc` erişimi `Method1` tanımlanan yöntemi `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="95b81-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="95b81-141">Genellikle, devralma hiyerarşilerini istenen davranışı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="95b81-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="95b81-142">Türetilmiş sınıftan türetilen bir sınıfta tanımlanan yöntemleri kullanmak için oluşturduğunuz değerlerine sahip nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95b81-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="95b81-143">Kullanarak bu davranışı elde `override` temel sınıf yöntemini genişletmek için.</span><span class="sxs-lookup"><span data-stu-id="95b81-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="95b81-144">Aşağıdaki kod tam örneği içermektedir.</span><span class="sxs-lookup"><span data-stu-id="95b81-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="95b81-145">Aşağıdaki örnek, farklı bir bağlamda benzer bir davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="95b81-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="95b81-146">Örnek üç sınıf tanımlar: adlı bir temel sınıf `Car` ve kendisinden üretilmiş iki sınıf `ConvertibleCar` ve `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="95b81-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="95b81-147">Taban sınıfı içeren bir `DescribeCar` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b81-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="95b81-148">Yöntemi, bir araba temel açıklamasını görüntüler ve ardından çağırır `ShowDetails` ek bilgi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="95b81-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="95b81-149">Üç sınıfların her birini tanımlayan bir `ShowDetails` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b81-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="95b81-150">`new` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `ConvertibleCar` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="95b81-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="95b81-151">`override` Değiştiricisi tanımlamak için kullanılan `ShowDetails` içinde `Minivan` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="95b81-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="95b81-152">Örnek hangi sürümünün testlerini `ShowDetails` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95b81-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="95b81-153">Aşağıdaki yöntem `TestCars1`her sınıfın bir örneği bildirir ve ardından çağırır `DescribeCar` her örneğinde.</span><span class="sxs-lookup"><span data-stu-id="95b81-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="95b81-154">`TestCars1` aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="95b81-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="95b81-155">Sonuçları özellikle dikkat edin `car2`, büyük olasılıkla olduğu beklediğiniz değil.</span><span class="sxs-lookup"><span data-stu-id="95b81-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="95b81-156">Nesne türü `ConvertibleCar`, ancak `DescribeCar` sürümünü erişmez `ShowDetails` içinde tanımlanan `ConvertibleCar` bu yöntem ile bildirildiğinden sınıf `new` değiştiricisi değil `override` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="95b81-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="95b81-157">Sonuç olarak, bir `ConvertibleCar` nesne görüntüler aynı açıklama olarak bir `Car` nesne.</span><span class="sxs-lookup"><span data-stu-id="95b81-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="95b81-158">Sonuçları Karşıtlık `car3`, olduğu bir `Minivan` nesne.</span><span class="sxs-lookup"><span data-stu-id="95b81-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="95b81-159">Bu durumda, `ShowDetails` bölümünde bildirilen yöntemi `Minivan` sınıf geçersiz kılmalarını `ShowDetails` bölümünde bildirilen yöntemi `Car` sınıfı ve görüntülenen açıklamayı bir minivan açıklar.</span><span class="sxs-lookup"><span data-stu-id="95b81-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="95b81-160">`TestCars2` türü olan nesnelerin bir listesini oluşturur `Car`.</span><span class="sxs-lookup"><span data-stu-id="95b81-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="95b81-161">Nesne değerlerini örneği oluşturulur `Car`, `ConvertibleCar`, ve `Minivan` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="95b81-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="95b81-162">`DescribeCar` Listedeki her öğe üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95b81-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="95b81-163">Aşağıdaki kod tanımını gösterir `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="95b81-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="95b81-164">Aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="95b81-164">The following output is displayed.</span></span> <span data-ttu-id="95b81-165">Tarafından görüntülenen çıktı ile aynı olduğunu fark `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="95b81-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="95b81-166">`ShowDetails` Yöntemi `ConvertibleCar` sınıfı çağrılmaz; nesne türü olmasına bakılmaksızın `ConvertibleCar`, olarak `TestCars1`, veya `Car`, olarak `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="95b81-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="95b81-167">Buna karşılık, `car3` çağrıları `ShowDetails` yönteminden `Minivan` türüne sahip olup olmadığını her iki durumda da, sınıf `Minivan` veya türü `Car`.</span><span class="sxs-lookup"><span data-stu-id="95b81-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="95b81-168">Yöntemleri `TestCars3` ve `TestCars4` örnek tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="95b81-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="95b81-169">Bu yöntemleri çağırmak `ShowDetails` doğrudan, ilk nesnelerden bildirilen türü olmasını `ConvertibleCar` ve `Minivan` (`TestCars3`), ardından türü için bildirilen nesnelerden `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="95b81-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="95b81-170">Aşağıdaki kod, bu iki yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="95b81-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="95b81-171">Yöntemler, bu konudaki ilk örnekte karşılık gelen sonuçları aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="95b81-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="95b81-172">Aşağıdaki kod tam projeyi ve çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95b81-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95b81-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95b81-173">See also</span></span>

- [<span data-ttu-id="95b81-174">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95b81-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="95b81-175">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="95b81-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="95b81-176">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="95b81-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="95b81-177">base</span><span class="sxs-lookup"><span data-stu-id="95b81-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="95b81-178">abstract</span><span class="sxs-lookup"><span data-stu-id="95b81-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)
