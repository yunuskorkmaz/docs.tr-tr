---
title: Sınıflar- C# Programlama Kılavuzu
description: Sınıf türleri ve bunların nasıl oluşturulacağı hakkında bilgi edinin
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 832095e1d9712c85ad588836e8eba8f523719021
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714974"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="50503-103">Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="50503-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="50503-104">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="50503-104">Reference types</span></span>  
<span data-ttu-id="50503-105">[Sınıf](../../language-reference/keywords/class.md) olarak tanımlanan bir tür, *başvuru türüdür*.</span><span class="sxs-lookup"><span data-stu-id="50503-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="50503-106">Çalışma zamanında, bir başvuru türünde bir değişken bildirdiğinizde, [New](../../language-reference/operators/new-operator.md) işlecini kullanarak sınıfın bir örneğini açıkça oluşturana veya onu aşağıdaki örnekte gösterildiği gibi başka bir yerde oluşturulmuş olan uyumlu bir türde bir nesne atayarak, değişken [null](../../language-reference/keywords/null.md) değerini içerir:</span><span class="sxs-lookup"><span data-stu-id="50503-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="50503-107">Nesne oluşturulduğunda, söz konusu nesne için yönetilen yığında yeterli bellek ayrılır ve değişken yalnızca belirtilen nesnenin konumuna bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="50503-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="50503-108">Yönetilen yığında bulunan türler, her ikisi de ayrıldıklarında ve *çöp toplama*olarak bilinen clr 'nin otomatik bellek yönetimi işlevselliği tarafından geri kazanıyorsa ek yük gerektirir.</span><span class="sxs-lookup"><span data-stu-id="50503-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="50503-109">Ancak çöp toplama da yüksek oranda iyileştirilmiştir ve çoğu senaryoda bir performans sorunu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="50503-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="50503-110">Çöp toplama hakkında daha fazla bilgi için bkz. [Otomatik bellek yönetimi ve çöp toplama](../../../standard/garbage-collection/gc.md).</span><span class="sxs-lookup"><span data-stu-id="50503-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="50503-111">Sınıfları Bildirme</span><span class="sxs-lookup"><span data-stu-id="50503-111">Declaring Classes</span></span>

 <span data-ttu-id="50503-112">Sınıflar, aşağıdaki örnekte gösterildiği gibi, [Class](../../language-reference/keywords/class.md) anahtar sözcüğü ve ardından benzersiz bir tanımlayıcı kullanılarak bildirilenler:</span><span class="sxs-lookup"><span data-stu-id="50503-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="50503-113">`class` anahtar kelimesinin öncesinde erişim düzeyi vardır.</span><span class="sxs-lookup"><span data-stu-id="50503-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="50503-114">Bu durumda [genel](../../language-reference/keywords/public.md) kullanıldığından, herkes bu sınıfın örneklerini oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="50503-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="50503-115">Sınıfın adı `class` anahtar sözcüğünü izler.</span><span class="sxs-lookup"><span data-stu-id="50503-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="50503-116">Sınıfın adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50503-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="50503-117">Tanımın geri kalanı, davranışın ve verilerin tanımlandığı sınıf gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="50503-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="50503-118">Bir sınıftaki alanlar, özellikler, Yöntemler ve olaylar topluca *sınıf üyeleri*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="50503-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="50503-119">Nesneler oluşturma</span><span class="sxs-lookup"><span data-stu-id="50503-119">Creating objects</span></span>

<span data-ttu-id="50503-120">Bazen birbirinin yerine kullanıldıkları halde bir sınıf ve bir nesne farklı şeylerdir.</span><span class="sxs-lookup"><span data-stu-id="50503-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="50503-121">Bir sınıf nesne türünü tanımlar, ancak nesnenin kendisi değildir.</span><span class="sxs-lookup"><span data-stu-id="50503-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="50503-122">Bir nesne, bir sınıfı temel alan somut bir varlıktır ve bazen bir sınıfın örneği olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="50503-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="50503-123">Nesneler [Yeni](../../language-reference/operators/new-operator.md) anahtar sözcüğü kullanılarak, ardından nesnenin temel aldığı sınıfın adı tarafından oluşturulabilir ve şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="50503-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="50503-124">Bir sınıfın bir örneği oluşturulduğunda, nesnesine bir başvuru, programcıya geri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="50503-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="50503-125">Önceki örnekte, `object1` `Customer`tabanlı bir nesneye başvurudur.</span><span class="sxs-lookup"><span data-stu-id="50503-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="50503-126">Bu başvuru yeni nesneye başvurur ancak nesne verilerinin kendisini içermez.</span><span class="sxs-lookup"><span data-stu-id="50503-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="50503-127">Aslında, herhangi bir nesne oluşturmadan bir nesne başvurusu oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50503-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="50503-128">Bir nesneye başvurmayan bu gibi nesne başvuruları oluşturmanızı önermeyiz, çünkü bu başvuru, bu tür bir başvuruya erişim denemesi çalışma zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="50503-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="50503-129">Ancak, bu tür bir başvuru, yeni bir nesne oluşturarak ya da bunun gibi var olan bir nesneye atanarak bir nesneye başvurmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="50503-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="50503-130">Bu kod, her ikisi de aynı nesneye başvuran iki nesne başvurusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50503-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="50503-131">Bu nedenle, `object3` aracılığıyla yapılan nesne üzerindeki tüm değişiklikler, `object4`sonraki kullanımlarına yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="50503-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="50503-132">Sınıfları temel alan nesneler başvuruya göre başvurulduğu için sınıflar başvuru türleri olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="50503-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="50503-133">Sınıf devralma</span><span class="sxs-lookup"><span data-stu-id="50503-133">Class inheritance</span></span>  

<span data-ttu-id="50503-134">Sınıflar, nesne odaklı programlamanın temel bir özelliği olan *devralmayı*tamamen destekler.</span><span class="sxs-lookup"><span data-stu-id="50503-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="50503-135">Bir sınıf oluşturduğunuzda, [korumalı](../../language-reference/keywords/sealed.md)olarak tanımlanmayan diğer bir arabirim veya sınıftan kalıtımla alabilir ve diğer sınıflar sınıfınızdan devralınabilir ve sınıf sanal yöntemlerini geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="50503-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="50503-136">Devralma bir *türetme*kullanılarak gerçekleştirilir. Bu, bir sınıfın veri ve davranış devraldığı *temel sınıf* kullanılarak bildirildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50503-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="50503-137">Bir temel sınıf, bir iki nokta üst üste eklenerek ve türetilmiş sınıf adından sonra temel sınıfın adı aşağıdaki gibi olarak belirtilir:</span><span class="sxs-lookup"><span data-stu-id="50503-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="50503-138">Bir sınıf bir temel sınıf bildiriyorsa, oluşturucular hariç, taban sınıfın tüm üyelerini devralır.</span><span class="sxs-lookup"><span data-stu-id="50503-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="50503-139">Daha fazla bilgi için bkz. [Devralma](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="50503-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="50503-140">Aksine C++, içindeki C# bir sınıf yalnızca bir temel sınıftan doğrudan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="50503-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="50503-141">Ancak, bir temel sınıfın kendisi başka bir sınıftan devraldığı için, bir sınıf dolaylı olarak birden fazla temel sınıfı devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="50503-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="50503-142">Ayrıca, bir sınıf doğrudan birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="50503-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="50503-143">Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="50503-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="50503-144">Bir sınıf, [soyut](../../language-reference/keywords/abstract.md)olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="50503-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="50503-145">Soyut bir sınıf imza tanımına sahip ancak uygulamaya sahip olmayan soyut yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="50503-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="50503-146">Soyut sınıfların örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="50503-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="50503-147">Yalnızca soyut yöntemleri uygulayan türetilmiş sınıflar aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50503-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="50503-148">Buna karşılık, [korumalı](../../language-reference/keywords/sealed.md) bir sınıf diğer sınıfların bundan türemesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="50503-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="50503-149">Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="50503-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="50503-150">Sınıf tanımları, farklı kaynak dosyalar arasında bölünebilir.</span><span class="sxs-lookup"><span data-stu-id="50503-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="50503-151">Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="50503-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50503-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="50503-152">Example</span></span>

<span data-ttu-id="50503-153">Aşağıdaki örnek, bir [Otomatik uygulanan özellik](auto-implemented-properties.md), bir yöntem ve Oluşturucu olarak adlandırılan özel bir yöntem içeren bir ortak sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50503-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="50503-154">Daha fazla bilgi için bkz. [Özellikler](properties.md), [Yöntemler](methods.md)ve [oluşturucular](constructors.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="50503-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="50503-155">Daha sonra sınıfının örnekleri `new` anahtar sözcüğüyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="50503-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="50503-156">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="50503-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50503-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50503-157">See also</span></span>

- [<span data-ttu-id="50503-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="50503-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="50503-159">Nesne Odaklı Programlama</span><span class="sxs-lookup"><span data-stu-id="50503-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="50503-160">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="50503-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="50503-161">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="50503-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="50503-162">Üyeler</span><span class="sxs-lookup"><span data-stu-id="50503-162">Members</span></span>](members.md)
- [<span data-ttu-id="50503-163">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50503-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="50503-164">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="50503-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="50503-165">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="50503-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="50503-166">Nesneler</span><span class="sxs-lookup"><span data-stu-id="50503-166">Objects</span></span>](objects.md)
