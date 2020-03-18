---
title: statik değiştirici - C# Referans
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744666"
---
# <a name="static-c-reference"></a><span data-ttu-id="85ed6-102">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="85ed6-102">static (C# Reference)</span></span>

<span data-ttu-id="85ed6-103">`static` Belirli bir nesneye değil, türe ait statik bir üyeyi bildirmek için değiştirici'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="85ed6-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="85ed6-104">`static` Değiştirici sınıfları bildirmek `static` için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="85ed6-105">Sınıflarda, arabirimlerde ve yapılarda, değiştiriciyi `static` alanlara, yöntemlere, özelliklere, işleçlere, olaylara ve yapıcılara ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85ed6-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="85ed6-106">`static` Değiştirici dizinleyiciler veya sonlandırıcılar ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="85ed6-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="85ed6-107">Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="85ed6-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="85ed6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="85ed6-108">Example</span></span>

<span data-ttu-id="85ed6-109">Aşağıdaki sınıf olarak `static` bildirilir ve `static` yalnızca yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="85ed6-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="85ed6-110">Sabit veya tür bildirimi dolaylı `static` olarak üyedir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="85ed6-111">Bir `static` üye bir örnek aracılığıyla başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="85ed6-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="85ed6-112">Bunun yerine, tür adı ile başvurulan.</span><span class="sxs-lookup"><span data-stu-id="85ed6-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="85ed6-113">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="85ed6-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="85ed6-114">`static` Üyeye `x`başvurmak için, üyeaynı kapsamdaerişilebilir olmadığı sürece, `MyBaseC.MyStruct.x`tam nitelikli adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="85ed6-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="85ed6-115">Bir sınıfın örneği sınıfın tüm örnek alanlarının ayrı bir kopyasını içerse de, her `static` alanın yalnızca bir kopyası vardır.</span><span class="sxs-lookup"><span data-stu-id="85ed6-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="85ed6-116">Başvuru `static` yöntemlerini veya [`this`](this.md) özellik erişimcilerini kullanmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="85ed6-117">Anahtar `static` sözcük bir sınıfa uygulanırsa, sınıfın tüm `static`üyeleri .</span><span class="sxs-lookup"><span data-stu-id="85ed6-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="85ed6-118">Sınıflar, arabirimler `static` ve sınıflar `static` oluşturucuolabilir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="85ed6-119">Bir `static` oluşturucu program başladığında ve sınıf anında zaman arasında bir noktada denir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="85ed6-120">Anahtar `static` kelimenin Kullanımı C++'a göre daha sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="85ed6-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="85ed6-121">C++ anahtar sözcüğüyle karşılaştırmak için [bkz.](/cpp/cpp/storage-classes-cpp#static)</span><span class="sxs-lookup"><span data-stu-id="85ed6-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="85ed6-122">Üyeleri `static` göstermek için, bir şirket çalışanLarını temsil eden bir sınıfı düşünün.</span><span class="sxs-lookup"><span data-stu-id="85ed6-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="85ed6-123">Sınıfın çalışanları saymak için bir yöntem ve çalışan sayısını depolamak için bir alan içerdiğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="85ed6-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="85ed6-124">Hem yöntem hem de alan herhangi bir çalışan örneğine ait değildir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="85ed6-125">Bunun yerine, bir bütün olarak çalışanların sınıfına aittir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="85ed6-126">Sınıfın üyeleri olarak `static` ilan edilmelidirler.</span><span class="sxs-lookup"><span data-stu-id="85ed6-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="85ed6-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="85ed6-127">Example</span></span>

<span data-ttu-id="85ed6-128">Bu örnek, yeni bir çalışanın adını ve kimliğini okur, çalışan sayacını bir er ler halinde arttırarak yeni çalışan ve yeni çalışan sayısına ait bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85ed6-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="85ed6-129">Bu program klavyeden geçerli çalışan sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="85ed6-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="85ed6-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="85ed6-130">Example</span></span>

<span data-ttu-id="85ed6-131">Bu örnek, henüz bildirilmemiş `static` başka `static` bir alan kullanarak bir alanı başlatmanızı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85ed6-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="85ed6-132">`static` Alana açıkça bir değer atayana kadar sonuçlar tanımsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="85ed6-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="85ed6-133">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="85ed6-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="85ed6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85ed6-134">See also</span></span>

- [<span data-ttu-id="85ed6-135">C# Referans</span><span class="sxs-lookup"><span data-stu-id="85ed6-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="85ed6-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="85ed6-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="85ed6-137">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="85ed6-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="85ed6-138">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="85ed6-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="85ed6-139">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="85ed6-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
