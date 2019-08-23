---
title: Class anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 0c4fc9645e43f23e340804b46bbe8a5faa19525d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922386"
---
# <a name="class-c-reference"></a><span data-ttu-id="00ef5-102">class (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="00ef5-102">class (C# Reference)</span></span>

<span data-ttu-id="00ef5-103">Sınıflar, aşağıdaki örnekte gösterildiği gibi `class`anahtar sözcüğü kullanılarak bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="00ef5-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="00ef5-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00ef5-104">Remarks</span></span>

<span data-ttu-id="00ef5-105">İçinde C#yalnızca tekli devralmaya izin verilir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="00ef5-106">Diğer bir deyişle, bir sınıf yalnızca bir temel sınıftan uygulamayı devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="00ef5-107">Ancak, bir sınıf birden fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="00ef5-108">Aşağıdaki tabloda sınıf devralma ve arabirim uygulama örnekleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00ef5-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="00ef5-109">Devralma</span><span class="sxs-lookup"><span data-stu-id="00ef5-109">Inheritance</span></span>|<span data-ttu-id="00ef5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="00ef5-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="00ef5-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="00ef5-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="00ef5-112">Tek</span><span class="sxs-lookup"><span data-stu-id="00ef5-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="00ef5-113">Hiçbiri, iki arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="00ef5-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="00ef5-114">Tek, bir arabirim uygular</span><span class="sxs-lookup"><span data-stu-id="00ef5-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="00ef5-115">Diğer sınıflarda iç içe değil, bir ad alanı içinde doğrudan bildirdiğiniz sınıflar [ortak](./public.md) veya [iç](./internal.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="00ef5-116">Sınıflar varsayılan `internal` olarak ' dir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="00ef5-117">İç içe geçmiş sınıflar dahil olmak üzere sınıf üyeleri [ortak](public.md), [korumalı dahili](protected-internal.md), [korunan](protected.md), [dahili](internal.md), [özel](private.md)veya [özel korumalı](private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="00ef5-118">Üyeler varsayılan `private` olarak ' dir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-118">Members are `private` by default.</span></span>

<span data-ttu-id="00ef5-119">Daha fazla bilgi için bkz. [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="00ef5-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="00ef5-120">Tür parametrelerine sahip genel sınıfları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00ef5-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="00ef5-121">Daha fazla bilgi için bkz. [genel sınıflar](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="00ef5-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="00ef5-122">Bir sınıf, aşağıdaki üyelerin bildirimlerini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="00ef5-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="00ef5-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="00ef5-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="00ef5-124">Sabitler</span><span class="sxs-lookup"><span data-stu-id="00ef5-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="00ef5-125">Alanlar</span><span class="sxs-lookup"><span data-stu-id="00ef5-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="00ef5-126">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="00ef5-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="00ef5-127">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="00ef5-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="00ef5-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="00ef5-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="00ef5-129">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="00ef5-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="00ef5-130">İşleçler</span><span class="sxs-lookup"><span data-stu-id="00ef5-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="00ef5-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="00ef5-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="00ef5-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="00ef5-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="00ef5-133">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="00ef5-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="00ef5-134">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="00ef5-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="00ef5-135">Yapılar</span><span class="sxs-lookup"><span data-stu-id="00ef5-135">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="00ef5-136">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="00ef5-136">Enumerations</span></span>](../../programming-guide/enumeration-types.md)

## <a name="example"></a><span data-ttu-id="00ef5-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="00ef5-137">Example</span></span>

<span data-ttu-id="00ef5-138">Aşağıdaki örnek, sınıf alanları, oluşturucular ve yöntemlerinin bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="00ef5-139">Ayrıca, nesne örneğini oluşturmayı ve örnek verilerini yazdırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="00ef5-140">Bu örnekte, iki sınıf bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-140">In this example, two classes are declared.</span></span> <span data-ttu-id="00ef5-141">İlk sınıf `Child`olan, iki özel alan (`name` ve `age`), iki ortak Oluşturucu ve bir genel yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="00ef5-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="00ef5-142">İkinci sınıfı `StringTest`, öğesini içermesi `Main`için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00ef5-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="00ef5-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00ef5-143">Comments</span></span>

<span data-ttu-id="00ef5-144">Önceki örnekte özel alanlara (`name` ve `age`) yalnızca `Child` sınıfın genel yöntemiyle erişildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="00ef5-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="00ef5-145">Örneğin, aşağıdaki gibi bir ifade kullanarak alt öğenin adını `Main` yöntemden yazdıramazsınız:</span><span class="sxs-lookup"><span data-stu-id="00ef5-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="00ef5-146">' In `Child` `Main` özel üyelerine erişim, yalnızca sınıfının bir üyesi `Main` ise mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="00ef5-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="00ef5-147">Bir erişim değiştiricisi `private`olmayan bir sınıf içinde bildirildiği türler, bu nedenle bu örnekteki veri üyeleri anahtar sözcüğünün kaldırılmakta olması `private` durumunda olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="00ef5-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="00ef5-148">Son olarak, parametresiz Oluşturucu (`child3`) kullanılarak oluşturulan nesne için `age` , alanın varsayılan olarak sıfıra başlatıldığını fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="00ef5-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="00ef5-149">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="00ef5-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="00ef5-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00ef5-150">See also</span></span>

- [<span data-ttu-id="00ef5-151">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="00ef5-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="00ef5-152">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="00ef5-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="00ef5-153">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="00ef5-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="00ef5-154">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="00ef5-154">Reference Types</span></span>](./reference-types.md)
