---
title: Arabirim özellikleri-C# Programlama Kılavuzu
description: Özellikler C# ' deki bir arabirim üzerinde bildirilebilecek. Bu örnek, bir arabirim özelliği erişimcisi bildirir.
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864975"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="e5fdd-104">Arabirim Özellikleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e5fdd-104">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="e5fdd-105">Özellikler, bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-105">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="e5fdd-106">Aşağıdaki örnek bir arabirim özelliği erişimcisi bildirir:</span><span class="sxs-lookup"><span data-stu-id="e5fdd-106">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="e5fdd-107">Arabirim özelliklerinin genellikle gövdesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-107">Interface properties typically don't have a body.</span></span> <span data-ttu-id="e5fdd-108">Erişimciler, özelliğin okuma-yazma, salt okunurdur veya salt yazılır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-108">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="e5fdd-109">Sınıfların ve yapıların aksine, bir gövde olmadan erişimcileri bildirmek [Otomatik uygulanan bir özellik](auto-implemented-properties.md)bildirmez.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-109">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="e5fdd-110">C# 8,0 ' den başlayarak bir arabirim, özellikler dahil olmak üzere Üyeler için varsayılan bir uygulama tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-110">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="e5fdd-111">Arabirimler örnek veri alanlarını tanımlayamadığından, bir arabirimdeki özellik için varsayılan bir uygulamanın tanımlanması nadir bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-111">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="e5fdd-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5fdd-112">Example</span></span>

<span data-ttu-id="e5fdd-113">Bu örnekte, arabirimin `IEmployee` okuma-yazma özelliği, `Name` ve salt okunurdur özelliği vardır `Counter` .</span><span class="sxs-lookup"><span data-stu-id="e5fdd-113">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="e5fdd-114">Sınıfı `Employee` `IEmployee` arabirimini uygular ve bu iki özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-114">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="e5fdd-115">Program yeni bir çalışanın adını ve geçerli çalışan sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-115">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="e5fdd-116">Özelliğin, üyenin bildirildiği arabirime başvuruda bulunduğu tam nitelikli adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-116">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="e5fdd-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e5fdd-117">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="e5fdd-118">Yukarıdaki örnekte [Açık arabirim uygulamaları](../interfaces/explicit-interface-implementation.md)gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-118">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="e5fdd-119">Örneğin, sınıfı `Employee` iki arabirim uygusa `ICitizen` `IEmployee` ve her iki arabirimde `Name` özelliği varsa, açık arabirim üye uygulaması gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-119">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="e5fdd-120">Diğer bir deyişle, aşağıdaki özellik bildirimi:</span><span class="sxs-lookup"><span data-stu-id="e5fdd-120">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="e5fdd-121">`Name` `IEmployee` aşağıdaki bildirim sırasında, özelliği arayüzde uygular:</span><span class="sxs-lookup"><span data-stu-id="e5fdd-121">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="e5fdd-122">`Name` `ICitizen` arabirimindeki özelliği arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-122">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="e5fdd-123">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="e5fdd-123">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="e5fdd-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5fdd-124">See also</span></span>

- [<span data-ttu-id="e5fdd-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e5fdd-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e5fdd-126">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5fdd-126">Properties</span></span>](./properties.md)
- [<span data-ttu-id="e5fdd-127">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e5fdd-127">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="e5fdd-128">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="e5fdd-128">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="e5fdd-129">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e5fdd-129">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="e5fdd-130">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e5fdd-130">Interfaces</span></span>](../interfaces/index.md)
