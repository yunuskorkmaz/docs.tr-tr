---
title: class anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: fbb685abcc5c2e79a64501385edf8f6c2041861d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662003"
---
# <a name="class-c-reference"></a><span data-ttu-id="b2aee-102">class (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b2aee-102">class (C# Reference)</span></span>

<span data-ttu-id="b2aee-103">Sınıflar, anahtar sözcüğü kullanılarak bildirilir `class`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="b2aee-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="b2aee-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2aee-104">Remarks</span></span>

<span data-ttu-id="b2aee-105">C# ' de yalnızca tek devralma izin verilir.</span><span class="sxs-lookup"><span data-stu-id="b2aee-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="b2aee-106">Diğer bir deyişle, bir sınıf bir taban sınıftan yalnızca uygulama devralabilir.</span><span class="sxs-lookup"><span data-stu-id="b2aee-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="b2aee-107">Ancak, bir sınıf birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="b2aee-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="b2aee-108">Aşağıdaki tablo, sınıf devralma ve arabirim uygulaması örneklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="b2aee-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="b2aee-109">Devralma</span><span class="sxs-lookup"><span data-stu-id="b2aee-109">Inheritance</span></span>|<span data-ttu-id="b2aee-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2aee-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="b2aee-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2aee-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="b2aee-112">Tek</span><span class="sxs-lookup"><span data-stu-id="b2aee-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="b2aee-113">None, iki arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="b2aee-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="b2aee-114">Tek bir arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="b2aee-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="b2aee-115">Diğer sınıflar içinde iç içe değil doğrudan bir ad alanındaki bildirdiğiniz sınıf ya da olabilir [genel](../../../csharp/language-reference/keywords/public.md) veya [iç](../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="b2aee-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="b2aee-116">Sınıflar `internal` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="b2aee-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="b2aee-117">İç içe geçmiş sınıflar, sınıf üyelerini olabilir [genel](public.md), [iç korumalı](protected-internal.md), [korumalı](protected.md), [iç](internal.md), [ özel](private.md), veya [korunan özel](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="b2aee-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="b2aee-118">Üyeleri `private` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="b2aee-118">Members are `private` by default.</span></span>

<span data-ttu-id="b2aee-119">Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b2aee-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="b2aee-120">Tür parametrelerine sahip Genel sınıflar bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2aee-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="b2aee-121">Daha fazla bilgi için [Genel sınıflar](../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b2aee-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="b2aee-122">Bir sınıf bildirimleri aşağıdaki üyeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b2aee-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="b2aee-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b2aee-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="b2aee-124">Sabitler</span><span class="sxs-lookup"><span data-stu-id="b2aee-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="b2aee-125">Alanlar</span><span class="sxs-lookup"><span data-stu-id="b2aee-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="b2aee-126">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="b2aee-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="b2aee-127">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2aee-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="b2aee-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b2aee-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="b2aee-129">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b2aee-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="b2aee-130">İşleçler</span><span class="sxs-lookup"><span data-stu-id="b2aee-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="b2aee-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b2aee-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="b2aee-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="b2aee-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="b2aee-133">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b2aee-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="b2aee-134">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b2aee-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="b2aee-135">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b2aee-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="b2aee-136">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b2aee-136">Enumerations</span></span>](../../../csharp/programming-guide/enumeration-types.md)

## <a name="example"></a><span data-ttu-id="b2aee-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2aee-137">Example</span></span>

<span data-ttu-id="b2aee-138">Aşağıdaki örnek, bildirim sınıfı alanlar, Oluşturucular ve yöntemler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2aee-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="b2aee-139">Ayrıca, nesne örneklemesini ve yazdırma örneği verileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2aee-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="b2aee-140">Bu örnekte, iki sınıf olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="b2aee-140">In this example, two classes are declared.</span></span> <span data-ttu-id="b2aee-141">İlk sınıf `Child`, iki özel alan içeriyor (`name` ve `age`), iki genel oluşturucular ve bir genel yöntem.</span><span class="sxs-lookup"><span data-stu-id="b2aee-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="b2aee-142">İkinci sınıfı `StringTest`, kapsamak için kullanılmış `Main`.</span><span class="sxs-lookup"><span data-stu-id="b2aee-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="b2aee-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2aee-143">Comments</span></span>

<span data-ttu-id="b2aee-144">Önceki örnekte dikkat özel alanlar (`name` ve `age`) yalnızca genel yöntemi aracılığıyla erişilebilir `Child` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2aee-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="b2aee-145">Gelen çocuğunuzun adı, örneğin, yazdıramıyorum `Main` yöntemi, şunun gibi bir deyim kullanarak:</span><span class="sxs-lookup"><span data-stu-id="b2aee-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="b2aee-146">Özel üyelerine erişme `Child` gelen `Main` yalnızca sağlayabileceğinizden varsa `Main` sınıfının üyesi olan.</span><span class="sxs-lookup"><span data-stu-id="b2aee-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="b2aee-147">Türleri bildirilen bir erişim değiştiricisi varsayılan olmayan bir sınıf içinde `private`, bu örnekte veri üyeleri olmaya `private` anahtar sözcüğü kaldırdıysanız.</span><span class="sxs-lookup"><span data-stu-id="b2aee-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="b2aee-148">Son olarak, parametresiz bir oluşturucu kullanılarak oluşturulan nesne için dikkat edin (`child3`), `age` alan sıfır olarak başlatılmış varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="b2aee-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b2aee-149">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b2aee-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b2aee-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2aee-150">See also</span></span>

- [<span data-ttu-id="b2aee-151">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b2aee-151">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="b2aee-152">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b2aee-152">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b2aee-153">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b2aee-153">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="b2aee-154">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="b2aee-154">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
