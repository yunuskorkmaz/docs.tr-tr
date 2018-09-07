---
title: Sınıflar (C# Programlama Kılavuzu)
description: Sınıf türleri ve bunların nasıl oluşturulacağı hakkında bilgi edinin
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: db490225bbef4517c1306aee7afb5c01d2d0fec6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081482"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="81370-103">Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="81370-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="81370-104">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="81370-104">Reference types</span></span>  
<span data-ttu-id="81370-105">Olarak tanımlanan bir tür bir [sınıfı](../../../csharp/language-reference/keywords/class.md) olduğu bir *başvuru türüne*.</span><span class="sxs-lookup"><span data-stu-id="81370-105">A type that is defined as a [class](../../../csharp/language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="81370-106">Bir değişken bildirdiğinizde başvuru türü, çalışma zamanında değişken değeri içeren [null](../../../csharp/language-reference/keywords/null.md) açıkça kullanarak sınıfının bir örneğini oluşturana kadar [yeni](../../../csharp/language-reference/keywords/new.md) işleci veya bir nesne atama bir başka bir yerde, aşağıdaki örnekte gösterildiği gibi oluşturulmuş olabilir uyumlu türü:</span><span class="sxs-lookup"><span data-stu-id="81370-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../../csharp/language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../../csharp/language-reference/keywords/new.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring a object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="81370-107">Nesne oluşturulduğunda, yeterli bellek, belirli bir nesnesi için yönetilen yığında ayrılır ve değişken yalnızca söz konusu nesnenin konumuna yönelik bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="81370-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="81370-108">Yönetilen yığındaki türler ayrıldıkları zaman hem olarak da bilinen CLR'nin otomatik bellek yönetimi işlevinin tarafından talep edilen zaman ek yükü gerektirir *çöp toplama*.</span><span class="sxs-lookup"><span data-stu-id="81370-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="81370-109">Ancak, çöp toplama yüksek oranda iyileştirilmiştir ve çoğu senaryoda, bir performans sorununa neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="81370-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="81370-110">Çöp toplama hakkında daha fazla bilgi için bkz: [otomatik bellek yönetimi ve çöp toplama](../../../standard/garbage-collection/gc.md).</span><span class="sxs-lookup"><span data-stu-id="81370-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="81370-111">Sınıfları Bildirme</span><span class="sxs-lookup"><span data-stu-id="81370-111">Declaring Classes</span></span>

 <span data-ttu-id="81370-112">Sınıfları kullanarak bildirilir [sınıfı](../../../csharp/language-reference/keywords/class.md) benzersiz bir tanımlayıcı aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü:</span><span class="sxs-lookup"><span data-stu-id="81370-112">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="81370-113">`class` Anahtar sözcüğü erişim düzeyi tarafından öncesinde.</span><span class="sxs-lookup"><span data-stu-id="81370-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="81370-114">Çünkü [genel](../../language-reference/keywords/public.md) kullanılan herkes bu sınıfın örnekleri, bu durumda, oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81370-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="81370-115">Sınıf adını izleyen `class` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="81370-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="81370-116">Sınıfın adı geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="81370-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="81370-117">Tanımı geri kalanında sınıfı, davranış ve veri tanımlandığı gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="81370-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="81370-118">Alanlar, özellikler, yöntemler ve olaylar sınıfta topluca denir *sınıf üyeleri*.</span><span class="sxs-lookup"><span data-stu-id="81370-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="81370-119">Nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="81370-119">Creating objects</span></span>

<span data-ttu-id="81370-120">Bazen kavramlarının birbirinin yerine kullanıldığı olsa da, bir sınıf ve nesne farklı noktalardır.</span><span class="sxs-lookup"><span data-stu-id="81370-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="81370-121">Bir nesne türüyle bir sınıf tanımlar, ancak bir nesne değil.</span><span class="sxs-lookup"><span data-stu-id="81370-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="81370-122">Bir nesne sınıfına göre somut bir varlık ve bazen bir sınıfın bir örneği da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="81370-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="81370-123">Nesneleri kullanarak oluşturulabilir [yeni](../../language-reference/keywords/new.md) anahtar sözcüğü bir nesne, temel sınıfın adını ardından şöyle:</span><span class="sxs-lookup"><span data-stu-id="81370-123">Objects can be created by using the [new](../../language-reference/keywords/new.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="81370-124">Bir sınıfın bir örneği oluşturulduğunda nesnesine bir başvuru programcıya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="81370-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="81370-125">Önceki örnekte, `object1` temel alan bir nesneye bir başvurudur `Customer`.</span><span class="sxs-lookup"><span data-stu-id="81370-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="81370-126">Bu başvuru yeni bir nesneye başvuruyor, ancak nesne verisi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="81370-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="81370-127">Aslında, bir nesne başvurusu bir nesne oluşturulmadan oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="81370-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="81370-128">Bunun gibi bir nesne gibi bir başvuru erişmeye çalışıyor, çalışma zamanında başarısız olacağı için bir nesneye başvuran olmayan nesne başvuruları oluşturmak önerilmemektedir.</span><span class="sxs-lookup"><span data-stu-id="81370-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="81370-129">Ancak, bir nesneye yeni bir nesne oluşturarak veya atayarak bu gibi varolan bir nesneye başvurmak için böyle bir başvuruyu yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="81370-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="81370-130">Bu kod, iki nesne başvuru oluşturur hem de aynı nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="81370-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="81370-131">Bu nedenle, nesne aracılığıyla yapılan değişiklikleri `object3` sonraki kullanımları içinde yansıtılır `object4`.</span><span class="sxs-lookup"><span data-stu-id="81370-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="81370-132">Sınıflara göre nesneleri başvuruya göre adlandırılır çünkü sınıflar başvuru türleri olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="81370-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="81370-133">Sınıf devralma</span><span class="sxs-lookup"><span data-stu-id="81370-133">Class inheritance</span></span>  

<span data-ttu-id="81370-134">Sınıfları tam destek *devralma*, nesne yönelimli programlama temel bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="81370-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="81370-135">Bir sınıf oluşturduğunuz zaman, herhangi bir arabirim veya tanımlanmamış sınıfı devralabilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md), ve diğer sınıflar, sizin sınıfınızdan miras ve sınıf sanal yöntemleri geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="81370-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../../csharp/language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="81370-136">Devralma kullanılarak gerçekleştirilir bir *türetme*, yani bir sınıf kullanılarak bildirilen bir *temel sınıfı* aldığı verilerini ve davranışlarını devralır.</span><span class="sxs-lookup"><span data-stu-id="81370-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="81370-137">Bir temel sınıf, bir iki nokta üst üste ve bunun gibi türetilmiş sınıf adını izleyen temel sınıfın adını ekleyerek belirtilir:</span><span class="sxs-lookup"><span data-stu-id="81370-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="81370-138">Bir sınıf bir taban sınıfı bildirir, temel sınıf oluşturucuları dışındaki tüm üyelerini devralır.</span><span class="sxs-lookup"><span data-stu-id="81370-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="81370-139">Daha fazla bilgi için [devralma](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="81370-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="81370-140">C++ programında farklı olarak, C# ' ta bir sınıf yalnızca doğrudan bir taban sınıftan devralabilir.</span><span class="sxs-lookup"><span data-stu-id="81370-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="81370-141">Ancak, bir temel sınıf kendisi başka bir sınıftan devralabilir olduğundan, bir sınıf dolaylı olarak birden çok taban sınıfı devralabilir.</span><span class="sxs-lookup"><span data-stu-id="81370-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="81370-142">Ayrıca, bir sınıf doğrudan birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="81370-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="81370-143">Daha fazla bilgi için [arabirimleri](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="81370-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="81370-144">Bir sınıf bildirilebilir [soyut](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="81370-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="81370-145">Bir Özet sınıf, bir imza tanımı ancak hiçbir uygulama soyut yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="81370-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="81370-146">Soyut sınıflar oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="81370-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="81370-147">Soyut yöntemlerini uygulayan türetilmiş sınıfları yalnızca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81370-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="81370-148">Bunun aksine, bir [korumalı](../../language-reference/keywords/sealed.md) sınıfı diğer sınıfların türetmeniz izin vermez.</span><span class="sxs-lookup"><span data-stu-id="81370-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="81370-149">Daha fazla bilgi için [soyut ve korumalı sınıflar ve sınıf üyeleri](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="81370-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="81370-150">Sınıf tanımları farklı kaynak dosyaları arasında bölünebilir.</span><span class="sxs-lookup"><span data-stu-id="81370-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="81370-151">Daha fazla bilgi için [kısmi sınıflar ve yöntemler](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="81370-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81370-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="81370-152">Example</span></span>

<span data-ttu-id="81370-153">Aşağıdaki örnek, içeren genel bir sınıf tanımlar. bir [otomatik uygulanan özellik](auto-implemented-properties.md), bir yöntem ve oluşturucu olarak adlandırılan özel bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="81370-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="81370-154">Daha fazla bilgi için [özellikleri](properties.md), [yöntemleri](methods.md), ve [oluşturucular](constructors.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="81370-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="81370-155">Sınıf örnekleri, ile örneği oluşturulur `new` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="81370-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="81370-156">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="81370-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81370-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81370-157">See Also</span></span>

- [<span data-ttu-id="81370-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="81370-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="81370-159">Nesne Odaklı Programlama</span><span class="sxs-lookup"><span data-stu-id="81370-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="81370-160">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="81370-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="81370-161">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="81370-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="81370-162">Üyeler</span><span class="sxs-lookup"><span data-stu-id="81370-162">Members</span></span>](members.md)
- [<span data-ttu-id="81370-163">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="81370-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="81370-164">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="81370-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="81370-165">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="81370-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="81370-166">Nesneler</span><span class="sxs-lookup"><span data-stu-id="81370-166">Objects</span></span>](objects.md)
