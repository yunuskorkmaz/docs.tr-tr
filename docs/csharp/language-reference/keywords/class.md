---
description: Class anahtar sözcüğü-C# başvurusu
title: Class anahtar sözcüğü-C# başvurusu
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 67c9c4be55cce25edf9ecb84b257a8523f193bec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142121"
---
# <a name="class-c-reference"></a><span data-ttu-id="5e7ca-103">class (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5e7ca-103">class (C# Reference)</span></span>

<span data-ttu-id="5e7ca-104">Sınıflar `class` , aşağıdaki örnekte gösterildiği gibi anahtar sözcüğü kullanılarak bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5e7ca-104">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="5e7ca-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e7ca-105">Remarks</span></span>

<span data-ttu-id="5e7ca-106">C# içinde yalnızca tek devralmaya izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-106">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="5e7ca-107">Diğer bir deyişle, bir sınıf yalnızca bir temel sınıftan uygulamayı devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-107">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="5e7ca-108">Ancak, bir sınıf birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-108">However, a class can implement more than one interface.</span></span> <span data-ttu-id="5e7ca-109">Aşağıdaki tabloda sınıf devralma ve arabirim uygulama örnekleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5e7ca-109">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="5e7ca-110">Devralma</span><span class="sxs-lookup"><span data-stu-id="5e7ca-110">Inheritance</span></span>|<span data-ttu-id="5e7ca-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e7ca-111">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="5e7ca-112">Yok</span><span class="sxs-lookup"><span data-stu-id="5e7ca-112">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="5e7ca-113">Tek</span><span class="sxs-lookup"><span data-stu-id="5e7ca-113">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="5e7ca-114">Hiçbiri, iki arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="5e7ca-114">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="5e7ca-115">Tek, bir arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="5e7ca-115">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="5e7ca-116">Diğer sınıflarda iç içe değil, bir ad alanı içinde doğrudan bildirdiğiniz sınıflar [ortak](./public.md) veya [iç](./internal.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-116">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="5e7ca-117">Sınıflar `internal` Varsayılan olarak ' dir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-117">Classes are `internal` by default.</span></span>

<span data-ttu-id="5e7ca-118">İç içe geçmiş sınıflar dahil olmak üzere sınıf üyeleri [ortak](public.md), [korumalı dahili](protected-internal.md), [korunan](protected.md), [dahili](internal.md), [özel](private.md)veya [özel korumalı](private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-118">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="5e7ca-119">Üyeler `private` Varsayılan olarak ' dir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-119">Members are `private` by default.</span></span>

<span data-ttu-id="5e7ca-120">Daha fazla bilgi için bkz. [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="5e7ca-120">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="5e7ca-121">Tür parametrelerine sahip genel sınıfları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-121">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="5e7ca-122">Daha fazla bilgi için bkz. [genel sınıflar](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5e7ca-122">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="5e7ca-123">Bir sınıf, aşağıdaki üyelerin bildirimlerini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="5e7ca-123">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="5e7ca-124">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5e7ca-124">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="5e7ca-125">Sabitler</span><span class="sxs-lookup"><span data-stu-id="5e7ca-125">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="5e7ca-126">Alanlar</span><span class="sxs-lookup"><span data-stu-id="5e7ca-126">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="5e7ca-127">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="5e7ca-127">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="5e7ca-128">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5e7ca-128">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="5e7ca-129">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5e7ca-129">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="5e7ca-130">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5e7ca-130">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="5e7ca-131">İşleçler</span><span class="sxs-lookup"><span data-stu-id="5e7ca-131">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="5e7ca-132">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="5e7ca-132">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="5e7ca-133">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5e7ca-133">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="5e7ca-134">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="5e7ca-134">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="5e7ca-135">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="5e7ca-135">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="5e7ca-136">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="5e7ca-136">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="5e7ca-137">Numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="5e7ca-137">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="5e7ca-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e7ca-138">Example</span></span>

<span data-ttu-id="5e7ca-139">Aşağıdaki örnek, sınıf alanları, oluşturucular ve yöntemlerinin bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-139">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="5e7ca-140">Ayrıca, nesne örneğini oluşturmayı ve örnek verilerini yazdırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-140">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="5e7ca-141">Bu örnekte, iki sınıf bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-141">In this example, two classes are declared.</span></span> <span data-ttu-id="5e7ca-142">İlk sınıf olan, `Child` iki özel alan ( `name` ve `age` ), iki ortak Oluşturucu ve bir genel yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-142">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="5e7ca-143">İkinci sınıfı, `StringTest` öğesini içermesi için kullanılır `Main` .</span><span class="sxs-lookup"><span data-stu-id="5e7ca-143">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="5e7ca-144">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="5e7ca-144">Comments</span></span>

<span data-ttu-id="5e7ca-145">Önceki örnekte özel alanlara ( `name` ve `age` ) yalnızca sınıfın genel yöntemiyle erişildiğine dikkat edin `Child` .</span><span class="sxs-lookup"><span data-stu-id="5e7ca-145">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="5e7ca-146">Örneğin, `Main` aşağıdaki gibi bir ifade kullanarak alt öğenin adını yöntemden yazdıramazsınız:</span><span class="sxs-lookup"><span data-stu-id="5e7ca-146">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="5e7ca-147">' In özel üyelerine erişim, `Child` `Main` yalnızca `Main` sınıfının bir üyesi ise mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-147">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="5e7ca-148">Bir erişim değiştiricisi olmayan bir sınıf içinde bildirildiği türler `private` , bu nedenle bu örnekteki veri üyeleri `private` anahtar sözcüğünün kaldırılmakta olması durumunda olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-148">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="5e7ca-149">Son olarak, parametresiz Oluşturucu () kullanılarak oluşturulan nesne için `child3` , `age` alanın varsayılan olarak sıfıra başlatıldığını fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-149">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5e7ca-150">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5e7ca-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5e7ca-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e7ca-151">See also</span></span>

- [<span data-ttu-id="5e7ca-152">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5e7ca-152">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5e7ca-153">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5e7ca-153">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5e7ca-154">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5e7ca-154">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="5e7ca-155">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="5e7ca-155">Reference Types</span></span>](./reference-types.md)
