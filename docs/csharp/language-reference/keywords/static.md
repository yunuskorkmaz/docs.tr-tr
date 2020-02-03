---
title: statik değiştirici C# başvurusu
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744666"
---
# <a name="static-c-reference"></a><span data-ttu-id="d552a-102">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d552a-102">static (C# Reference)</span></span>

<span data-ttu-id="d552a-103">Belirli bir nesne yerine türüne ait olan statik bir üye bildirmek için `static` değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d552a-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="d552a-104">`static` değiştiricisi `static` sınıfları bildirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d552a-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="d552a-105">Sınıflarda, arabirimlerde ve yapılarda `static` değiştiricisini alanlara, yöntemlere, özelliklere, işleçlere, olaylara ve oluşturuculara ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d552a-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="d552a-106">`static` değiştiricisi Dizin oluşturucular veya sonlandırıcılar ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d552a-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="d552a-107">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d552a-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="d552a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d552a-108">Example</span></span>

<span data-ttu-id="d552a-109">Aşağıdaki sınıf `static` olarak bildirilmiştir ve yalnızca `static` yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d552a-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="d552a-110">Sabit veya tür bildirimi örtük olarak bir `static` üyesidir.</span><span class="sxs-lookup"><span data-stu-id="d552a-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="d552a-111">Bir `static` üyesine bir örnek üzerinden başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="d552a-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="d552a-112">Bunun yerine tür adı ile başvurulur.</span><span class="sxs-lookup"><span data-stu-id="d552a-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="d552a-113">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d552a-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="d552a-114">`static` üye `x`başvurmak için, üyenin aynı kapsamdan erişilebilir olmadığı durumlar `MyBaseC.MyStruct.x`tam adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="d552a-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="d552a-115">Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her bir `static` alanın yalnızca bir kopyası vardır.</span><span class="sxs-lookup"><span data-stu-id="d552a-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="d552a-116">`static` yöntemlere veya özellik erişimcilerine başvurmak için [`this`](this.md) kullanılması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d552a-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="d552a-117">`static` anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri `static`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d552a-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="d552a-118">Sınıflar, arabirimler ve `static` sınıfları `static` oluşturuculara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d552a-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="d552a-119">`static` Oluşturucusu, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d552a-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="d552a-120">`static` anahtar sözcüğü, öğesinden daha sınırlı kullanımları vardır C++.</span><span class="sxs-lookup"><span data-stu-id="d552a-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="d552a-121">Anahtar sözcükle karşılaştırmak için bkz. [Depolama sınıfları (C++).](/cpp/cpp/storage-classes-cpp#static) C++</span><span class="sxs-lookup"><span data-stu-id="d552a-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="d552a-122">`static` üyelerini göstermek için, bir şirket çalışanını temsil eden bir sınıf düşünün.</span><span class="sxs-lookup"><span data-stu-id="d552a-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="d552a-123">Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="d552a-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="d552a-124">Hem yöntemi hem de alanı bir çalışan örneğine ait değildir.</span><span class="sxs-lookup"><span data-stu-id="d552a-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="d552a-125">Bunun yerine, çalışanlar sınıfına bir bütün olarak aittir.</span><span class="sxs-lookup"><span data-stu-id="d552a-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="d552a-126">Sınıfın `static` üyesi olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d552a-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="d552a-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d552a-127">Example</span></span>

<span data-ttu-id="d552a-128">Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d552a-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="d552a-129">Bu program, klavyeden geçerli çalışan sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="d552a-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="d552a-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d552a-130">Example</span></span>

<span data-ttu-id="d552a-131">Bu örnek, henüz bildirilmemiş başka bir `static` alanını kullanarak bir `static` alanı başlatabilmeniz gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d552a-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="d552a-132">`static` alana açıkça bir değer atamaz kadar sonuçlar tanımsız olur.</span><span class="sxs-lookup"><span data-stu-id="d552a-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="d552a-133">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d552a-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d552a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d552a-134">See also</span></span>

- [<span data-ttu-id="d552a-135">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="d552a-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d552a-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d552a-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d552a-137">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d552a-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d552a-138">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="d552a-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d552a-139">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="d552a-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
