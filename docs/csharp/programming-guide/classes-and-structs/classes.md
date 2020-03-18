---
title: Sınıflar - C# Programlama Kılavuzu
description: Sınıf türleri ve bunları nasıl oluşturabilirsiniz hakkında bilgi edinin
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: aadf555fb47963eab323bbb6105227c5b119e6f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170318"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="052e0-103">Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="052e0-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="052e0-104">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="052e0-104">Reference types</span></span>  
<span data-ttu-id="052e0-105">[Sınıf](../../language-reference/keywords/class.md) olarak tanımlanan bir tür *bir başvuru türüdür.*</span><span class="sxs-lookup"><span data-stu-id="052e0-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="052e0-106">Çalışma zamanında, bir başvuru türüdeğişkenini beyan ettiğinizde, yeni [işleci](../../language-reference/operators/new-operator.md) kullanarak sınıfın bir örneğini açıkça oluşturana veya aşağıdaki örnekte gösterildiği gibi başka bir yerde oluşturulmuş olabilecek uyumlu bir türe ait bir nesne atayıncaya kadar değişken [geçersiz](../../language-reference/keywords/null.md) değer içerir:</span><span class="sxs-lookup"><span data-stu-id="052e0-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="052e0-107">Nesne oluşturulduğunda, yönetilen yığına belirli bir nesne için yeterli bellek ayrılır ve değişken yalnızca bu nesnenin konumuna bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="052e0-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="052e0-108">Yönetilen yığındaki türler, hem ayrıldıklarında hem de *çöp toplama*olarak bilinen CLR'nin otomatik bellek yönetimi işlevi tarafından geri alındıklarında ek yükü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="052e0-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="052e0-109">Ancak, çöp toplama da son derece iyi leştirilmiştir ve çoğu senaryoda bir performans sorunu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="052e0-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="052e0-110">Çöp toplama hakkında daha fazla bilgi için [Otomatik bellek yönetimi ve çöp toplama](../../../standard/garbage-collection/gc.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="052e0-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="052e0-111">Sınıfları Bildirme</span><span class="sxs-lookup"><span data-stu-id="052e0-111">Declaring Classes</span></span>

 <span data-ttu-id="052e0-112">Sınıflar, aşağıdaki örnekte gösterildiği [gibi, sınıf](../../language-reference/keywords/class.md) anahtar sözcüğü kullanılarak ve ardından benzersiz bir tanımlayıcı kullanılarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="052e0-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="052e0-113">Anahtar `class` kelimenin önünde erişim düzeyi gelir.</span><span class="sxs-lookup"><span data-stu-id="052e0-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="052e0-114">Bu durumda [genel](../../language-reference/keywords/public.md) olarak kullanıldığından, herkes bu sınıfın örneklerini oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="052e0-115">Sınıfın adı anahtar sözcüğü `class` izler.</span><span class="sxs-lookup"><span data-stu-id="052e0-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="052e0-116">Sınıfın adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="052e0-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="052e0-117">Tanımın geri kalanı, davranış ve verilerin tanımlandığı sınıf gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="052e0-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="052e0-118">Bir sınıftaki alanlar, özellikler, yöntemler ve olaylar topluca *sınıf üyeleri*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="052e0-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="052e0-119">Nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="052e0-119">Creating objects</span></span>

<span data-ttu-id="052e0-120">Bazen birbirlerinin yerine kullanılmasına rağmen, bir sınıf ve bir nesne farklı şeylerdir.</span><span class="sxs-lookup"><span data-stu-id="052e0-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="052e0-121">Bir sınıf bir nesne türünü tanımlar, ancak nesnenin kendisi değildir.</span><span class="sxs-lookup"><span data-stu-id="052e0-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="052e0-122">Nesne, bir sınıfa dayalı somut bir varlıktır ve bazen bir sınıfın örneği olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="052e0-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="052e0-123">Nesneler, nesnenin temel alacağı sınıfın adını izleyen [yeni](../../language-reference/operators/new-operator.md) anahtar sözcük kullanılarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="052e0-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="052e0-124">Bir sınıf örneği oluşturulduğunda, nesneye yapılan bir başvuru programcıya geri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="052e0-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="052e0-125">Önceki örnekte, `object1` `Customer`'yi temel alan bir nesneye başvuru</span><span class="sxs-lookup"><span data-stu-id="052e0-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="052e0-126">Bu başvuru yeni nesneye başvurur, ancak nesne verisinin kendisini içermez.</span><span class="sxs-lookup"><span data-stu-id="052e0-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="052e0-127">Aslında, hiç bir nesne oluşturmadan bir nesne başvurusu oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="052e0-127">In fact, you can create an object reference without creating an object at all:</span></span>  

```csharp
 Customer object2;
```

 <span data-ttu-id="052e0-128">Böyle bir başvuru aracılığıyla bir nesneye erişmeye çalışmak çalışma zamanında başarısız olacağından, bir nesneye başvurmadan bunun gibi nesne başvuruları oluşturmanızı önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="052e0-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="052e0-129">Ancak, böyle bir başvuru, yeni bir nesne oluşturarak veya aşağıdaki gibi varolan bir nesneye atayarak bir nesneye başvurmak için yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="052e0-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="052e0-130">Bu kod, her ikisi de aynı nesneye başvuran iki nesne başvurur.</span><span class="sxs-lookup"><span data-stu-id="052e0-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="052e0-131">Bu nedenle, nesne üzerinden `object3` yapılan herhangi bir değişiklik `object4`sonraki kullanımlarında yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="052e0-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="052e0-132">Sınıfları temel alan nesneler referans olarak anılacaktır, sınıflar başvuru türleri olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="052e0-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="052e0-133">Sınıf kalıbı</span><span class="sxs-lookup"><span data-stu-id="052e0-133">Class inheritance</span></span>  

<span data-ttu-id="052e0-134">Sınıflar, nesne yönelimli programlamanın temel bir özelliği olan *kalıtımı*tam olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="052e0-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="052e0-135">Bir sınıf oluşturduğunuzda, [mühürlü](../../language-reference/keywords/sealed.md)olarak tanımlanmayan başka bir arabirim veya sınıftan devralabilir ve diğer sınıflar sınıfınızdan devralabilir ve sınıf sanal yöntemlerini geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="052e0-136">Devralma bir *türetme*kullanılarak gerçekleştirilir , yani bir sınıf, verileri ve davranışı devraldığı bir *taban sınıf* kullanılarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="052e0-137">Bir taban sınıf, bir üst üste ve türemiş sınıf adını izleyen taban sınıfın adını ekleyerek şu şekilde belirtilir:</span><span class="sxs-lookup"><span data-stu-id="052e0-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="052e0-138">Bir sınıf bir taban sınıf beyan ettiğinde, oluşturucular dışında taban sınıfın tüm üyelerini devralır.</span><span class="sxs-lookup"><span data-stu-id="052e0-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="052e0-139">Daha fazla bilgi için [Bkz. Kalıtım.](inheritance.md)</span><span class="sxs-lookup"><span data-stu-id="052e0-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="052e0-140">C++'ın aksine, C#'daki bir sınıf yalnızca doğrudan bir taban sınıftan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="052e0-141">Ancak, bir taban sınıf başka bir sınıftan devralabileceğinden, bir sınıf dolaylı olarak birden çok temel sınıfı devralabilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="052e0-142">Ayrıca, bir sınıf doğrudan birden fazla arabirim uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="052e0-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="052e0-143">Daha fazla bilgi için [Arabirimler'e](../interfaces/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="052e0-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="052e0-144">Bir sınıf [soyut](../../language-reference/keywords/abstract.md)olarak ilan edilebilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="052e0-145">Soyut bir sınıf, imza tanımı na sahip ancak uygulama olmayan soyut yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="052e0-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="052e0-146">Soyut sınıflar anında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="052e0-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="052e0-147">Bunlar yalnızca soyut yöntemleri uygulayan türemiş sınıflar aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="052e0-148">Bunun aksine, [mühürlü](../../language-reference/keywords/sealed.md) bir sınıf diğer sınıfların ondan türemesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="052e0-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="052e0-149">Daha fazla bilgi için [Bkz. Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri.](abstract-and-sealed-classes-and-class-members.md)</span><span class="sxs-lookup"><span data-stu-id="052e0-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="052e0-150">Sınıf tanımları farklı kaynak dosyaları arasında bölünebilir.</span><span class="sxs-lookup"><span data-stu-id="052e0-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="052e0-151">Daha fazla bilgi için Kısmi [Sınıflar ve Yöntemler'e](partial-classes-and-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="052e0-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="052e0-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="052e0-152">Example</span></span>

<span data-ttu-id="052e0-153">Aşağıdaki örnek, otomatik olarak uygulanan bir [özellik,](auto-implemented-properties.md)bir yöntem ve oluşturucu adı verilen özel bir yöntem içeren ortak bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="052e0-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="052e0-154">Daha fazla bilgi için [Özellikler,](properties.md) [Yöntemler](methods.md)ve [Kurucular](constructors.md) konularına bakın.</span><span class="sxs-lookup"><span data-stu-id="052e0-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="052e0-155">Sınıfın örnekleri daha sonra `new` anahtar kelime ile anında.</span><span class="sxs-lookup"><span data-stu-id="052e0-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="052e0-156">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="052e0-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="052e0-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="052e0-157">See also</span></span>

- [<span data-ttu-id="052e0-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="052e0-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="052e0-159">Nesne Odaklı Programlama</span><span class="sxs-lookup"><span data-stu-id="052e0-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="052e0-160">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="052e0-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="052e0-161">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="052e0-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="052e0-162">Üyeler</span><span class="sxs-lookup"><span data-stu-id="052e0-162">Members</span></span>](members.md)
- [<span data-ttu-id="052e0-163">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="052e0-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="052e0-164">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="052e0-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="052e0-165">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="052e0-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="052e0-166">Nesneler</span><span class="sxs-lookup"><span data-stu-id="052e0-166">Objects</span></span>](objects.md)
