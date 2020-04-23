---
title: statik değiştirici - C# Referans
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102066"
---
# <a name="static-c-reference"></a><span data-ttu-id="13e26-102">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="13e26-102">static (C# Reference)</span></span>

<span data-ttu-id="13e26-103">Bu sayfa `static` değiştirici anahtar sözcüğü kapsar.</span><span class="sxs-lookup"><span data-stu-id="13e26-103">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="13e26-104">`static` Anahtar kelime de yönergenin bir [`using static`](using-static.md) parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="13e26-104">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="13e26-105">`static` Belirli bir nesneye değil, türe ait statik bir üyeyi bildirmek için değiştirici'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="13e26-105">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="13e26-106">`static` Değiştirici sınıfları bildirmek `static` için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13e26-106">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="13e26-107">Sınıflarda, arabirimlerde ve yapılarda, değiştiriciyi `static` alanlara, yöntemlere, özelliklere, işleçlere, olaylara ve yapıcılara ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13e26-107">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="13e26-108">`static` Değiştirici dizinleyiciler veya sonlandırıcılar ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="13e26-108">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="13e26-109">Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="13e26-109">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="13e26-110">Örnek - statik sınıf</span><span class="sxs-lookup"><span data-stu-id="13e26-110">Example - static class</span></span>

<span data-ttu-id="13e26-111">Aşağıdaki sınıf olarak `static` bildirilir ve `static` yalnızca yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="13e26-111">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="13e26-112">Sabit veya tür bildirimi dolaylı `static` olarak üyedir.</span><span class="sxs-lookup"><span data-stu-id="13e26-112">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="13e26-113">Bir `static` üye bir örnek aracılığıyla başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="13e26-113">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="13e26-114">Bunun yerine, tür adı ile başvurulan.</span><span class="sxs-lookup"><span data-stu-id="13e26-114">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="13e26-115">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="13e26-115">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="13e26-116">`static` Üyeye `x`başvurmak için, üyeaynı kapsamdaerişilebilir olmadığı sürece, `MyBaseC.MyStruct.x`tam nitelikli adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="13e26-116">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="13e26-117">Bir sınıfın örneği sınıfın tüm örnek alanlarının ayrı bir kopyasını içerse de, her `static` alanın yalnızca bir kopyası vardır.</span><span class="sxs-lookup"><span data-stu-id="13e26-117">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="13e26-118">Başvuru `static` yöntemlerini veya [`this`](this.md) özellik erişimcilerini kullanmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="13e26-118">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="13e26-119">Anahtar `static` sözcük bir sınıfa uygulanırsa, sınıfın tüm `static`üyeleri .</span><span class="sxs-lookup"><span data-stu-id="13e26-119">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="13e26-120">Sınıflar, arabirimler `static` ve sınıflar `static` oluşturucuolabilir.</span><span class="sxs-lookup"><span data-stu-id="13e26-120">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="13e26-121">Bir `static` oluşturucu program başladığında ve sınıf anında zaman arasında bir noktada denir.</span><span class="sxs-lookup"><span data-stu-id="13e26-121">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="13e26-122">Anahtar `static` kelimenin Kullanımı C++'a göre daha sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="13e26-122">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="13e26-123">C++ anahtar sözcüğüyle karşılaştırmak için [bkz.](/cpp/cpp/storage-classes-cpp#static)</span><span class="sxs-lookup"><span data-stu-id="13e26-123">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="13e26-124">Üyeleri `static` göstermek için, bir şirket çalışanLarını temsil eden bir sınıfı düşünün.</span><span class="sxs-lookup"><span data-stu-id="13e26-124">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="13e26-125">Sınıfın çalışanları saymak için bir yöntem ve çalışan sayısını depolamak için bir alan içerdiğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="13e26-125">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="13e26-126">Hem yöntem hem de alan herhangi bir çalışan örneğine ait değildir.</span><span class="sxs-lookup"><span data-stu-id="13e26-126">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="13e26-127">Bunun yerine, bir bütün olarak çalışanların sınıfına aittir.</span><span class="sxs-lookup"><span data-stu-id="13e26-127">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="13e26-128">Sınıfın üyeleri olarak `static` ilan edilmelidirler.</span><span class="sxs-lookup"><span data-stu-id="13e26-128">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="13e26-129">Örnek - statik alan ve yöntem</span><span class="sxs-lookup"><span data-stu-id="13e26-129">Example - static field and method</span></span>

<span data-ttu-id="13e26-130">Bu örnek, yeni bir çalışanın adını ve kimliğini okur, çalışan sayacını bir er ler halinde arttırarak yeni çalışan ve yeni çalışan sayısına ait bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="13e26-130">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="13e26-131">Bu program klavyeden geçerli çalışan sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="13e26-131">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="13e26-132">Örnek - statik başlatma</span><span class="sxs-lookup"><span data-stu-id="13e26-132">Example - static initialization</span></span>

<span data-ttu-id="13e26-133">Bu örnek, henüz bildirilmemiş `static` başka `static` bir alan kullanarak bir alanı başlatmanızı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="13e26-133">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="13e26-134">`static` Alana açıkça bir değer atayana kadar sonuçlar tanımsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="13e26-134">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="13e26-135">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="13e26-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="13e26-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13e26-136">See also</span></span>

- [<span data-ttu-id="13e26-137">C# Referans</span><span class="sxs-lookup"><span data-stu-id="13e26-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13e26-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="13e26-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13e26-139">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="13e26-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="13e26-140">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="13e26-140">Modifiers</span></span>](index.md)
- [<span data-ttu-id="13e26-141">statik yönergeyi kullanarak</span><span class="sxs-lookup"><span data-stu-id="13e26-141">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="13e26-142">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="13e26-142">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
