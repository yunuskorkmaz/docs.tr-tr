---
title: Arabirim özellikleri- C# Programlama Kılavuzu
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626626"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="14bd3-102">Arabirim Özellikleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="14bd3-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="14bd3-103">Özellikler, bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="14bd3-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="14bd3-104">Aşağıdaki örnek bir arabirim özelliği erişimcisi bildirir:</span><span class="sxs-lookup"><span data-stu-id="14bd3-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="14bd3-105">Arabirim özelliklerinin genellikle gövdesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="14bd3-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="14bd3-106">Erişimciler, özelliğin okuma-yazma, salt okunurdur veya salt yazılır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="14bd3-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="14bd3-107">Sınıfların ve yapıların aksine, bir gövde olmadan erişimcileri bildirmek [Otomatik uygulanan bir özellik](auto-implemented-properties.md)bildirmez.</span><span class="sxs-lookup"><span data-stu-id="14bd3-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="14bd3-108">8,0 ile C# başlayarak, bir arabirim, özellikler dahil olmak üzere Üyeler için varsayılan bir uygulama tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="14bd3-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="14bd3-109">Arabirimler örnek veri alanlarını tanımlayamadığından, bir arabirimdeki özellik için varsayılan bir uygulamanın tanımlanması nadir bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="14bd3-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="14bd3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="14bd3-110">Example</span></span>

<span data-ttu-id="14bd3-111">Bu örnekte, `IEmployee` arabirim, bir okuma-yazma özelliğine, `Name`ve salt okunurdur bir özelliğe sahiptir `Counter`.</span><span class="sxs-lookup"><span data-stu-id="14bd3-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="14bd3-112">Sınıf `Employee` `IEmployee` arabirimini uygular ve bu iki özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="14bd3-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="14bd3-113">Program yeni bir çalışanın adını ve geçerli çalışan sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="14bd3-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="14bd3-114">Özelliğin, üyenin bildirildiği arabirime başvuruda bulunduğu tam nitelikli adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14bd3-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="14bd3-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="14bd3-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="14bd3-116">Yukarıdaki örnekte [Açık arabirim uygulamaları](../interfaces/explicit-interface-implementation.md)gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="14bd3-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="14bd3-117">Örneğin, sınıfı `Employee` iki arabirimi `ICitizen` ve `IEmployee` ve her iki arabirimde de `Name` özelliği varsa, açık arabirim üye uygulaması gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="14bd3-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="14bd3-118">Diğer bir deyişle, aşağıdaki özellik bildirimi:</span><span class="sxs-lookup"><span data-stu-id="14bd3-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="14bd3-119">, aşağıdaki bildirim sırasında `IEmployee` arabirimindeki `Name` özelliğini uygular:</span><span class="sxs-lookup"><span data-stu-id="14bd3-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="14bd3-120">`ICitizen` arabirimindeki `Name` özelliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="14bd3-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="14bd3-121">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="14bd3-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="14bd3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14bd3-122">See also</span></span>

- [<span data-ttu-id="14bd3-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="14bd3-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="14bd3-124">Özellikler</span><span class="sxs-lookup"><span data-stu-id="14bd3-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="14bd3-125">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="14bd3-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="14bd3-126">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="14bd3-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="14bd3-127">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="14bd3-127">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="14bd3-128">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="14bd3-128">Interfaces</span></span>](../interfaces/index.md)
