---
description: statik değiştirici-C# başvurusu
title: statik değiştirici-C# başvurusu
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f42636d1bbdf4342297f46f50ec6dfc2a70eacad
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142069"
---
# <a name="static-c-reference"></a><span data-ttu-id="b6e9b-103">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b6e9b-103">static (C# Reference)</span></span>

<span data-ttu-id="b6e9b-104">Bu sayfa `static` değiştirici anahtar sözcüğünü içerir.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="b6e9b-105">`static`Anahtar sözcüğü ayrıca yönergesinin bir parçasıdır [`using static`](using-static.md) .</span><span class="sxs-lookup"><span data-stu-id="b6e9b-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="b6e9b-106">Belirli bir `static` nesne yerine türüne ait olan statik bir üye bildirmek için değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="b6e9b-107">`static`Değiştirici, sınıfları bildirmek için kullanılabilir `static` .</span><span class="sxs-lookup"><span data-stu-id="b6e9b-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="b6e9b-108">Sınıflar, arabirimler ve yapılar ' da `static` alanları, yöntemleri, özellikleri, işleçleri, olayları ve oluşturuculara değiştiricisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="b6e9b-109">`static`Değiştirici, Dizin oluşturucular veya sonlandırıcılar ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="b6e9b-110">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="b6e9b-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="b6e9b-111">Örnek-statik sınıf</span><span class="sxs-lookup"><span data-stu-id="b6e9b-111">Example - static class</span></span>

<span data-ttu-id="b6e9b-112">Aşağıdaki sınıf olarak bildirilmiştir `static` ve yalnızca `static` yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b6e9b-112">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="b6e9b-113">Sabit veya tür bildirimi örtük olarak bir `static` üyedir.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-113">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="b6e9b-114">Bir `static` üyeye bir örnek üzerinden başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-114">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="b6e9b-115">Bunun yerine tür adı ile başvurulur.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-115">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="b6e9b-116">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b6e9b-116">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="b6e9b-117">Üyeye başvurmak için, `static` `x` `MyBaseC.MyStruct.x` üyenin aynı kapsamdan erişilebilir olmadığı durumlar dışında tam adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="b6e9b-117">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="b6e9b-118">Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her alanın yalnızca bir kopyası vardır `static` .</span><span class="sxs-lookup"><span data-stu-id="b6e9b-118">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="b6e9b-119">[`this`](this.md) `static` Yöntemlere veya özellik erişimcilerine başvurmak için kullanılması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-119">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="b6e9b-120">`static`Anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri olmalıdır `static` .</span><span class="sxs-lookup"><span data-stu-id="b6e9b-120">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="b6e9b-121">Sınıflar, arabirimler ve `static` sınıflar oluşturuculara sahip olabilir `static` .</span><span class="sxs-lookup"><span data-stu-id="b6e9b-121">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="b6e9b-122">Bir `static` Oluşturucu, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-122">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="b6e9b-123">`static`Anahtar sözcüğünün C++ ' dan daha fazla sınırlı kullanımı vardır.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-123">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="b6e9b-124">C++ anahtar sözcüğüyle karşılaştırmak için bkz. [Depolama sınıfları (c++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="b6e9b-124">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="b6e9b-125">Üyeleri göstermek için `static` , bir şirket çalışanını temsil eden bir sınıf düşünün.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-125">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="b6e9b-126">Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-126">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="b6e9b-127">Hem yöntemi hem de alanı bir çalışan örneğine ait değildir.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-127">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="b6e9b-128">Bunun yerine, çalışanlar sınıfına bir bütün olarak aittir.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-128">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="b6e9b-129">`static`Sınıfın üyeleri olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-129">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="b6e9b-130">Örnek-statik alan ve Yöntem</span><span class="sxs-lookup"><span data-stu-id="b6e9b-130">Example - static field and method</span></span>

<span data-ttu-id="b6e9b-131">Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-131">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="b6e9b-132">Bu program, klavyeden geçerli çalışan sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-132">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="b6e9b-133">Örnek-statik başlatma</span><span class="sxs-lookup"><span data-stu-id="b6e9b-133">Example - static initialization</span></span>

<span data-ttu-id="b6e9b-134">Bu örnek, `static` henüz bildirilmemiş olan başka bir alanı kullanarak bir alanı başlatabilmeniz gerektiğini gösterir `static` .</span><span class="sxs-lookup"><span data-stu-id="b6e9b-134">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="b6e9b-135">Alana açıkça bir değer atanana kadar sonuçlar tanımsız olur `static` .</span><span class="sxs-lookup"><span data-stu-id="b6e9b-135">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="b6e9b-136">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b6e9b-136">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b6e9b-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6e9b-137">See also</span></span>

- [<span data-ttu-id="b6e9b-138">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b6e9b-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b6e9b-139">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b6e9b-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b6e9b-140">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b6e9b-140">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b6e9b-141">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="b6e9b-141">Modifiers</span></span>](index.md)
- [<span data-ttu-id="b6e9b-142">static yönergesini kullanma</span><span class="sxs-lookup"><span data-stu-id="b6e9b-142">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="b6e9b-143">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="b6e9b-143">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
