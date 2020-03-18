---
title: sınıf anahtar kelime - C# Referans
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673101"
---
# <a name="class-c-reference"></a><span data-ttu-id="7b599-102">class (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7b599-102">class (C# Reference)</span></span>

<span data-ttu-id="7b599-103">Sınıflar, aşağıdaki örnekte `class`gösterildiği gibi anahtar kelime kullanılarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="7b599-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="7b599-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b599-104">Remarks</span></span>

<span data-ttu-id="7b599-105">C#'da yalnızca tek bir devralmaya izin verilir.</span><span class="sxs-lookup"><span data-stu-id="7b599-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="7b599-106">Başka bir deyişle, bir sınıf yalnızca bir taban sınıftan uygulama devralabilir.</span><span class="sxs-lookup"><span data-stu-id="7b599-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="7b599-107">Ancak, bir sınıf birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="7b599-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="7b599-108">Aşağıdaki tabloda sınıf devralma ve arabirim uygulama örnekleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7b599-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="7b599-109">Devralma</span><span class="sxs-lookup"><span data-stu-id="7b599-109">Inheritance</span></span>|<span data-ttu-id="7b599-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b599-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="7b599-111">None</span><span class="sxs-lookup"><span data-stu-id="7b599-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="7b599-112">Tek</span><span class="sxs-lookup"><span data-stu-id="7b599-112">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="7b599-113">Yok, iki arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="7b599-113">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="7b599-114">Tek, bir arayüz uygular</span><span class="sxs-lookup"><span data-stu-id="7b599-114">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="7b599-115">Diğer sınıflar içinde iç içe olmayan, doğrudan bir ad alanı içinde beyan ettiğiniz [sınıflar, genel](./public.md) veya [dahili](./internal.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b599-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="7b599-116">Sınıflar `internal` varsayılan olarak vardır.</span><span class="sxs-lookup"><span data-stu-id="7b599-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="7b599-117">İç içe sınıflar da dahil olmak üzere sınıf [üyeleri, kamu,](public.md) [korunan iç,](protected-internal.md) [korumalı,](protected.md) [iç,](internal.md) [özel](private.md)veya [özel korumalı](private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b599-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="7b599-118">Üyeler `private` varsayılan olarak vardır.</span><span class="sxs-lookup"><span data-stu-id="7b599-118">Members are `private` by default.</span></span>

<span data-ttu-id="7b599-119">Daha fazla bilgi için [Erişim Değiştiriciler'e](../../programming-guide/classes-and-structs/access-modifiers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7b599-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="7b599-120">Tür parametreleri olan genel sınıfları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b599-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="7b599-121">Daha fazla bilgi için [Genel Sınıflar'a](../../programming-guide/generics/generic-classes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7b599-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="7b599-122">Bir sınıf aşağıdaki üyelerin bildirimlerini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="7b599-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="7b599-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7b599-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="7b599-124">Sabitler</span><span class="sxs-lookup"><span data-stu-id="7b599-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="7b599-125">Alanlar</span><span class="sxs-lookup"><span data-stu-id="7b599-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="7b599-126">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="7b599-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="7b599-127">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7b599-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="7b599-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7b599-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="7b599-129">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7b599-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="7b599-130">İşleçler</span><span class="sxs-lookup"><span data-stu-id="7b599-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="7b599-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="7b599-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="7b599-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="7b599-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="7b599-133">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="7b599-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="7b599-134">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="7b599-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="7b599-135">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="7b599-135">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="7b599-136">Numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="7b599-136">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="7b599-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b599-137">Example</span></span>

<span data-ttu-id="7b599-138">Aşağıdaki örnek, sınıf alanlarını, oluşturucuları ve yöntemleri bildireni gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b599-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="7b599-139">Ayrıca nesne anlık ve yazdırma örneği verilerini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b599-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="7b599-140">Bu örnekte, iki sınıf bildirilir.</span><span class="sxs-lookup"><span data-stu-id="7b599-140">In this example, two classes are declared.</span></span> <span data-ttu-id="7b599-141">Birinci sınıf, `Child`iki özel alan`name` `age`(ve), iki kamu yapıcılar ve bir ortak yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="7b599-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="7b599-142">İkinci sınıf, `StringTest`, içerdiği `Main`için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b599-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="7b599-143">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="7b599-143">Comments</span></span>

<span data-ttu-id="7b599-144">Önceki örnekte özel alanlara`name` (ve) `age`yalnızca `Child` sınıfın ortak yöntemiyle erişilenebildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7b599-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="7b599-145">Örneğin, aşağıdaki gibi bir ifade kullanarak `Main` yöntemden çocuğun adını yazdıramazsınız:</span><span class="sxs-lookup"><span data-stu-id="7b599-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="7b599-146">Özel `Child` üyelere `Main` yalnızca sınıfın bir `Main` üyesi olsaydı erişmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7b599-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="7b599-147">Erişim değiştiricisi varsayılan olarak bir sınıf `private`içinde bildirilen türler , bu `private` nedenle bu örnekteki veri üyeleri anahtar sözcük kaldırılırsa yine de olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7b599-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="7b599-148">Son olarak, parametresiz oluşturucu kullanılarak oluşturulan`child3`nesne `age` için alanın varsayılan olarak sıfıra başlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7b599-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7b599-149">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7b599-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b599-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b599-150">See also</span></span>

- [<span data-ttu-id="7b599-151">C# Referans</span><span class="sxs-lookup"><span data-stu-id="7b599-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b599-152">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7b599-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b599-153">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="7b599-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="7b599-154">Referans Türleri</span><span class="sxs-lookup"><span data-stu-id="7b599-154">Reference Types</span></span>](./reference-types.md)
