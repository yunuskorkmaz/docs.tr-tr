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
ms.openlocfilehash: 239163fc2f91ccbfe8b1c111a358db87d36a8308
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654645"
---
# <a name="static-c-reference"></a><span data-ttu-id="3e125-103">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3e125-103">static (C# Reference)</span></span>

<span data-ttu-id="3e125-104">Bu sayfa `static` değiştirici anahtar sözcüğünü içerir.</span><span class="sxs-lookup"><span data-stu-id="3e125-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="3e125-105">`static`Anahtar sözcüğü ayrıca yönergesinin bir parçasıdır [`using static`](using-static.md) .</span><span class="sxs-lookup"><span data-stu-id="3e125-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="3e125-106">Belirli bir `static` nesne yerine türüne ait olan statik bir üye bildirmek için değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e125-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="3e125-107">`static`Değiştirici, sınıfları bildirmek için kullanılabilir `static` .</span><span class="sxs-lookup"><span data-stu-id="3e125-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="3e125-108">Sınıflar, arabirimler ve yapılar ' da `static` alanları, yöntemleri, özellikleri, işleçleri, olayları ve oluşturuculara değiştiricisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e125-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="3e125-109">`static`Değiştirici, Dizin oluşturucular veya sonlandırıcılar ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e125-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="3e125-110">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="3e125-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="3e125-111">C# 8,0 ' den başlayarak, `static` değiştirici bir [Yerel işleve](../../programming-guide/classes-and-structs/local-functions.md)eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e125-111">Beginning with C# 8.0, you can add the `static` modifier to a [local function](../../programming-guide/classes-and-structs/local-functions.md).</span></span> <span data-ttu-id="3e125-112">Statik bir yerel işlev yerel değişkenler veya örnek durumu yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="3e125-112">A static local function can't capture local variables or instance state.</span></span>

<span data-ttu-id="3e125-113">C# 9,0 ' den başlayarak `static` bir [lambda ifadesine](../operators/lambda-expressions.md) veya [anonim yönteme](../operators/delegate-operator.md)değiştirici ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e125-113">Beginning with C# 9.0, you can add the `static` modifier to a [lambda expression](../operators/lambda-expressions.md) or [anonymous method](../operators/delegate-operator.md).</span></span> <span data-ttu-id="3e125-114">Statik lambda veya anonim yöntem yerel değişkenleri veya örnek durumunu yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="3e125-114">A static lambda or anonymous method can't capture local variables or instance state.</span></span>

## <a name="example---static-class"></a><span data-ttu-id="3e125-115">Örnek-statik sınıf</span><span class="sxs-lookup"><span data-stu-id="3e125-115">Example - static class</span></span>

<span data-ttu-id="3e125-116">Aşağıdaki sınıf olarak bildirilmiştir `static` ve yalnızca `static` yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3e125-116">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="3e125-117">Sabit veya tür bildirimi örtük olarak bir `static` üyedir.</span><span class="sxs-lookup"><span data-stu-id="3e125-117">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="3e125-118">Bir `static` üyeye bir örnek üzerinden başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="3e125-118">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="3e125-119">Bunun yerine tür adı ile başvurulur.</span><span class="sxs-lookup"><span data-stu-id="3e125-119">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="3e125-120">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3e125-120">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="3e125-121">Üyeye başvurmak için, `static` `x` `MyBaseC.MyStruct.x` üyenin aynı kapsamdan erişilebilir olmadığı durumlar dışında tam adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="3e125-121">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="3e125-122">Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her alanın yalnızca bir kopyası vardır `static` .</span><span class="sxs-lookup"><span data-stu-id="3e125-122">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="3e125-123">[`this`](this.md) `static` Yöntemlere veya özellik erişimcilerine başvurmak için kullanılması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="3e125-123">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="3e125-124">`static`Anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri olmalıdır `static` .</span><span class="sxs-lookup"><span data-stu-id="3e125-124">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="3e125-125">Sınıflar, arabirimler ve `static` sınıflar oluşturuculara sahip olabilir `static` .</span><span class="sxs-lookup"><span data-stu-id="3e125-125">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="3e125-126">Bir `static` Oluşturucu, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3e125-126">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="3e125-127">`static`Anahtar sözcüğünün C++ ' dan daha fazla sınırlı kullanımı vardır.</span><span class="sxs-lookup"><span data-stu-id="3e125-127">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="3e125-128">C++ anahtar sözcüğüyle karşılaştırmak için bkz. [Depolama sınıfları (c++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="3e125-128">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="3e125-129">Üyeleri göstermek için `static` , bir şirket çalışanını temsil eden bir sınıf düşünün.</span><span class="sxs-lookup"><span data-stu-id="3e125-129">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="3e125-130">Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="3e125-130">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="3e125-131">Hem yöntemi hem de alanı bir çalışan örneğine ait değildir.</span><span class="sxs-lookup"><span data-stu-id="3e125-131">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="3e125-132">Bunun yerine, çalışanlar sınıfına bir bütün olarak aittir.</span><span class="sxs-lookup"><span data-stu-id="3e125-132">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="3e125-133">`static`Sınıfın üyeleri olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e125-133">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="3e125-134">Örnek-statik alan ve Yöntem</span><span class="sxs-lookup"><span data-stu-id="3e125-134">Example - static field and method</span></span>

<span data-ttu-id="3e125-135">Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3e125-135">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="3e125-136">Bu program, klavyeden geçerli çalışan sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="3e125-136">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="3e125-137">Örnek-statik başlatma</span><span class="sxs-lookup"><span data-stu-id="3e125-137">Example - static initialization</span></span>

<span data-ttu-id="3e125-138">Bu örnek, `static` henüz bildirilmemiş olan başka bir alanı kullanarak bir alanı başlatabilmeniz gerektiğini gösterir `static` .</span><span class="sxs-lookup"><span data-stu-id="3e125-138">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="3e125-139">Alana açıkça bir değer atanana kadar sonuçlar tanımsız olur `static` .</span><span class="sxs-lookup"><span data-stu-id="3e125-139">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="3e125-140">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3e125-140">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3e125-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e125-141">See also</span></span>

- [<span data-ttu-id="3e125-142">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3e125-142">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3e125-143">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3e125-143">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3e125-144">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3e125-144">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3e125-145">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="3e125-145">Modifiers</span></span>](index.md)
- [<span data-ttu-id="3e125-146">static yönergesini kullanma</span><span class="sxs-lookup"><span data-stu-id="3e125-146">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="3e125-147">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="3e125-147">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
