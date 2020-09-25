---
description: statik değiştirici-C# başvurusu
title: statik değiştirici-C# başvurusu
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: ccd575748c2286fa7348e2880acbfadd036d9ccd
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247728"
---
# <a name="static-c-reference"></a><span data-ttu-id="a3885-103">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a3885-103">static (C# Reference)</span></span>

<span data-ttu-id="a3885-104">Bu sayfa `static` değiştirici anahtar sözcüğünü içerir.</span><span class="sxs-lookup"><span data-stu-id="a3885-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="a3885-105">`static`Anahtar sözcüğü ayrıca yönergesinin bir parçasıdır [`using static`](using-static.md) .</span><span class="sxs-lookup"><span data-stu-id="a3885-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="a3885-106">Belirli bir `static` nesne yerine türüne ait olan statik bir üye bildirmek için değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a3885-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="a3885-107">`static`Değiştirici, sınıfları bildirmek için kullanılabilir `static` .</span><span class="sxs-lookup"><span data-stu-id="a3885-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="a3885-108">Sınıflar, arabirimler ve yapılar ' da `static` alanları, yöntemleri, özellikleri, işleçleri, olayları ve oluşturuculara değiştiricisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3885-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="a3885-109">`static`Değiştirici, Dizin oluşturucular veya sonlandırıcılar ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a3885-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="a3885-110">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="a3885-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="a3885-111">C# 9,0 ' den başlayarak `static` bir [lambda ifadesine](../operators/lambda-expressions.md) veya [anonim yönteme](../operators/delegate-operator.md)değiştirici ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3885-111">Beginning with C# 9.0, you can add the `static` modifier to a [lambda expression](../operators/lambda-expressions.md) or [anonymous method](../operators/delegate-operator.md).</span></span> <span data-ttu-id="a3885-112">Statik lambda veya anonim yöntem yerel değişkenleri veya örnek durumunu yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="a3885-112">A static lambda or anonymous method can't capture local variables or instance state.</span></span>

## <a name="example---static-class"></a><span data-ttu-id="a3885-113">Örnek-statik sınıf</span><span class="sxs-lookup"><span data-stu-id="a3885-113">Example - static class</span></span>

<span data-ttu-id="a3885-114">Aşağıdaki sınıf olarak bildirilmiştir `static` ve yalnızca `static` yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a3885-114">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="a3885-115">Sabit veya tür bildirimi örtük olarak bir `static` üyedir.</span><span class="sxs-lookup"><span data-stu-id="a3885-115">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="a3885-116">Bir `static` üyeye bir örnek üzerinden başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="a3885-116">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="a3885-117">Bunun yerine tür adı ile başvurulur.</span><span class="sxs-lookup"><span data-stu-id="a3885-117">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="a3885-118">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a3885-118">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="a3885-119">Üyeye başvurmak için, `static` `x` `MyBaseC.MyStruct.x` üyenin aynı kapsamdan erişilebilir olmadığı durumlar dışında tam adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="a3885-119">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="a3885-120">Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her alanın yalnızca bir kopyası vardır `static` .</span><span class="sxs-lookup"><span data-stu-id="a3885-120">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="a3885-121">[`this`](this.md) `static` Yöntemlere veya özellik erişimcilerine başvurmak için kullanılması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="a3885-121">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="a3885-122">`static`Anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri olmalıdır `static` .</span><span class="sxs-lookup"><span data-stu-id="a3885-122">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="a3885-123">Sınıflar, arabirimler ve `static` sınıflar oluşturuculara sahip olabilir `static` .</span><span class="sxs-lookup"><span data-stu-id="a3885-123">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="a3885-124">Bir `static` Oluşturucu, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a3885-124">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="a3885-125">`static`Anahtar sözcüğünün C++ ' dan daha fazla sınırlı kullanımı vardır.</span><span class="sxs-lookup"><span data-stu-id="a3885-125">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="a3885-126">C++ anahtar sözcüğüyle karşılaştırmak için bkz. [Depolama sınıfları (c++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="a3885-126">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="a3885-127">Üyeleri göstermek için `static` , bir şirket çalışanını temsil eden bir sınıf düşünün.</span><span class="sxs-lookup"><span data-stu-id="a3885-127">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="a3885-128">Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="a3885-128">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="a3885-129">Hem yöntemi hem de alanı bir çalışan örneğine ait değildir.</span><span class="sxs-lookup"><span data-stu-id="a3885-129">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="a3885-130">Bunun yerine, çalışanlar sınıfına bir bütün olarak aittir.</span><span class="sxs-lookup"><span data-stu-id="a3885-130">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="a3885-131">`static`Sınıfın üyeleri olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a3885-131">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="a3885-132">Örnek-statik alan ve Yöntem</span><span class="sxs-lookup"><span data-stu-id="a3885-132">Example - static field and method</span></span>

<span data-ttu-id="a3885-133">Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a3885-133">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="a3885-134">Bu program, klavyeden geçerli çalışan sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="a3885-134">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="a3885-135">Örnek-statik başlatma</span><span class="sxs-lookup"><span data-stu-id="a3885-135">Example - static initialization</span></span>

<span data-ttu-id="a3885-136">Bu örnek, `static` henüz bildirilmemiş olan başka bir alanı kullanarak bir alanı başlatabilmeniz gerektiğini gösterir `static` .</span><span class="sxs-lookup"><span data-stu-id="a3885-136">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="a3885-137">Alana açıkça bir değer atanana kadar sonuçlar tanımsız olur `static` .</span><span class="sxs-lookup"><span data-stu-id="a3885-137">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="a3885-138">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a3885-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a3885-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3885-139">See also</span></span>

- [<span data-ttu-id="a3885-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a3885-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a3885-141">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a3885-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a3885-142">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a3885-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a3885-143">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="a3885-143">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a3885-144">static yönergesini kullanma</span><span class="sxs-lookup"><span data-stu-id="a3885-144">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="a3885-145">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="a3885-145">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
