---
title: statik değiştirici C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f4ca3fcf809e723d2144654f1da949eb4d6de1b4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713072"
---
# <a name="static-c-reference"></a><span data-ttu-id="d6315-102">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d6315-102">static (C# Reference)</span></span>

<span data-ttu-id="d6315-103">Belirli bir nesne yerine türüne ait olan statik bir üye bildirmek için `static` değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d6315-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="d6315-104">`static` değiştiricisi sınıflar, alanlar, Yöntemler, özellikler, işleçler, olaylar ve oluşturucularla birlikte kullanılabilir, ancak sınıf dışındaki Dizin oluşturucular, sonlandırıcılar veya türler ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d6315-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="d6315-105">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d6315-105">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="d6315-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6315-106">Example</span></span>

<span data-ttu-id="d6315-107">Aşağıdaki sınıf `static` olarak bildirilmiştir ve yalnızca `static` yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d6315-107">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="d6315-108">Sabit veya tür bildirimi örtük olarak statik bir üyedir.</span><span class="sxs-lookup"><span data-stu-id="d6315-108">A constant or type declaration is implicitly a static member.</span></span>

<span data-ttu-id="d6315-109">Statik üyeye bir örnek üzerinden başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="d6315-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="d6315-110">Bunun yerine tür adı ile başvurulur.</span><span class="sxs-lookup"><span data-stu-id="d6315-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="d6315-111">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d6315-111">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="d6315-112">Statik üye `x`başvurmak için, üyenin aynı kapsamdan erişilebilir olmadığı müddetçe, `MyBaseC.MyStruct.x`tam adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="d6315-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="d6315-113">Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her statik alanın yalnızca bir kopyası vardır.</span><span class="sxs-lookup"><span data-stu-id="d6315-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>

<span data-ttu-id="d6315-114">Statik yöntemlere veya özellik erişimcilerine başvurmak için [bunu](this.md) kullanmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d6315-114">It is not possible to use [this](this.md) to reference static methods or property accessors.</span></span>

<span data-ttu-id="d6315-115">`static` anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri statik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6315-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>

<span data-ttu-id="d6315-116">Sınıflar ve statik sınıfların statik oluşturucuları olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6315-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="d6315-117">Statik oluşturucular, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d6315-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="d6315-118">`static` anahtar sözcüğü, öğesinden daha sınırlı kullanımları vardır C++.</span><span class="sxs-lookup"><span data-stu-id="d6315-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="d6315-119">Anahtar sözcükle karşılaştırmak için bkz. [Depolama sınıfları (C++).](/cpp/cpp/storage-classes-cpp#static) C++</span><span class="sxs-lookup"><span data-stu-id="d6315-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="d6315-120">Statik üyeleri göstermek için, bir şirket çalışanını temsil eden bir sınıf düşünün.</span><span class="sxs-lookup"><span data-stu-id="d6315-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="d6315-121">Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="d6315-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="d6315-122">Hem yöntem hem de alan herhangi bir örnek çalışana ait değildir.</span><span class="sxs-lookup"><span data-stu-id="d6315-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="d6315-123">Bunun yerine, şirket sınıfına ait olurlar.</span><span class="sxs-lookup"><span data-stu-id="d6315-123">Instead they belong to the company class.</span></span> <span data-ttu-id="d6315-124">Bu nedenle, sınıfın statik üyeleri olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d6315-124">Therefore, they should be declared as static members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="d6315-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6315-125">Example</span></span>

<span data-ttu-id="d6315-126">Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d6315-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="d6315-127">Kolaylık olması için, bu program klavyeden geçerli çalışan sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="d6315-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="d6315-128">Gerçek bir uygulamada, bu bilgiler bir dosyadan okunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6315-128">In a real application, this information should be read from a file.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="d6315-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6315-129">Example</span></span>

<span data-ttu-id="d6315-130">Bu örnek, henüz bildirilmemiş başka bir statik alanı kullanarak bir statik alanı başlatabilmenize karşın, statik alana açıkça bir değer atayana kadar sonuçlar tanımsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d6315-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="d6315-131">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d6315-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d6315-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6315-132">See also</span></span>

- [<span data-ttu-id="d6315-133">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="d6315-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d6315-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d6315-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d6315-135">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d6315-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d6315-136">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="d6315-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d6315-137">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="d6315-137">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
