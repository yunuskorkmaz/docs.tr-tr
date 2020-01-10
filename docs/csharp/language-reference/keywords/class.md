---
title: Class anahtar sözcüğü C# başvurusu
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 187a49131e903e00cab54d9db43b6cd8eb359a3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713685"
---
# <a name="class-c-reference"></a><span data-ttu-id="ad688-102">class (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ad688-102">class (C# Reference)</span></span>

<span data-ttu-id="ad688-103">Sınıflar, aşağıdaki örnekte gösterildiği gibi anahtar sözcük `class`kullanılarak bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ad688-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="ad688-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad688-104">Remarks</span></span>

<span data-ttu-id="ad688-105">İçinde C#yalnızca tekli devralmaya izin verilir.</span><span class="sxs-lookup"><span data-stu-id="ad688-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="ad688-106">Diğer bir deyişle, bir sınıf yalnızca bir temel sınıftan uygulamayı devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="ad688-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="ad688-107">Ancak, bir sınıf birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="ad688-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="ad688-108">Aşağıdaki tabloda sınıf devralma ve arabirim uygulama örnekleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ad688-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="ad688-109">Devralma</span><span class="sxs-lookup"><span data-stu-id="ad688-109">Inheritance</span></span>|<span data-ttu-id="ad688-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad688-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="ad688-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="ad688-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="ad688-112">Tek</span><span class="sxs-lookup"><span data-stu-id="ad688-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="ad688-113">Hiçbiri, iki arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="ad688-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="ad688-114">Tek, bir arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="ad688-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="ad688-115">Diğer sınıflarda iç içe değil, bir ad alanı içinde doğrudan bildirdiğiniz sınıflar [ortak](./public.md) veya [iç](./internal.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad688-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="ad688-116">Sınıflar varsayılan olarak `internal`.</span><span class="sxs-lookup"><span data-stu-id="ad688-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="ad688-117">İç içe geçmiş sınıflar dahil olmak üzere sınıf üyeleri [ortak](public.md), [korumalı dahili](protected-internal.md), [korunan](protected.md), [dahili](internal.md), [özel](private.md)veya [özel korumalı](private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad688-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="ad688-118">Üyeler varsayılan olarak `private`.</span><span class="sxs-lookup"><span data-stu-id="ad688-118">Members are `private` by default.</span></span>

<span data-ttu-id="ad688-119">Daha fazla bilgi için bkz. [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ad688-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="ad688-120">Tür parametrelerine sahip genel sınıfları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad688-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="ad688-121">Daha fazla bilgi için bkz. [genel sınıflar](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="ad688-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="ad688-122">Bir sınıf, aşağıdaki üyelerin bildirimlerini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="ad688-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="ad688-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ad688-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="ad688-124">Sabitler</span><span class="sxs-lookup"><span data-stu-id="ad688-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="ad688-125">Alanlar</span><span class="sxs-lookup"><span data-stu-id="ad688-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="ad688-126">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="ad688-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="ad688-127">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad688-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="ad688-128">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="ad688-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="ad688-129">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ad688-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="ad688-130">İşleçler</span><span class="sxs-lookup"><span data-stu-id="ad688-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="ad688-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ad688-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="ad688-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ad688-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="ad688-133">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="ad688-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="ad688-134">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ad688-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="ad688-135">Yapılar</span><span class="sxs-lookup"><span data-stu-id="ad688-135">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="ad688-136">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ad688-136">Enumerations</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="ad688-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad688-137">Example</span></span>

<span data-ttu-id="ad688-138">Aşağıdaki örnek, sınıf alanları, oluşturucular ve yöntemlerinin bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad688-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="ad688-139">Ayrıca, nesne örneğini oluşturmayı ve örnek verilerini yazdırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad688-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="ad688-140">Bu örnekte, iki sınıf bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ad688-140">In this example, two classes are declared.</span></span> <span data-ttu-id="ad688-141">İlk sınıf `Child`, iki özel alan (`name` ve `age`), iki ortak Oluşturucu ve bir genel yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="ad688-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="ad688-142">İkinci sınıf, `StringTest`, `Main`içermesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad688-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="ad688-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad688-143">Comments</span></span>

<span data-ttu-id="ad688-144">Önceki örnekte özel alanlara (`name` ve `age`) yalnızca `Child` sınıfının public yöntemi aracılığıyla erişildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ad688-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="ad688-145">Örneğin, aşağıdaki gibi bir ifade kullanarak, çocuğun adını `Main` yönteminden yazdıramıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="ad688-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="ad688-146">`Main` `Child` özel üyelerine erişmek, yalnızca `Main` sınıfının bir üyesi olması durumunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad688-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="ad688-147">Bir erişim değiştiricisi olmayan bir sınıf içinde belirtilen türler `private`için varsayılan olarak, bu örnekteki veri üyeleri anahtar sözcük kaldırılırsa `private` olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="ad688-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="ad688-148">Son olarak, parametresiz Oluşturucu (`child3`) kullanılarak oluşturulan nesne için, `age` alanın varsayılan olarak sıfırdan başlatıldığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ad688-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ad688-149">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ad688-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ad688-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad688-150">See also</span></span>

- [<span data-ttu-id="ad688-151">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="ad688-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ad688-152">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ad688-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ad688-153">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ad688-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="ad688-154">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="ad688-154">Reference Types</span></span>](./reference-types.md)
