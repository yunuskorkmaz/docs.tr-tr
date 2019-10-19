---
title: Arabirim özellikleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: fad674c6d56011afcccbe9ce2a88e7af411fe0a2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579150"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="a0b0f-102">Arabirim Özellikleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a0b0f-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="a0b0f-103">Özellikler, bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="a0b0f-104">Aşağıda bir arabirim özelliği erişimcisi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a0b0f-104">The following is an example of an interface property accessor:</span></span>

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

<span data-ttu-id="a0b0f-105">Bir arabirim özelliğinin erişimcisinin gövdesi yok.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="a0b0f-106">Bu nedenle, erişimcilerinin amacı, özelliğin okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>

## <a name="example"></a><span data-ttu-id="a0b0f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0b0f-107">Example</span></span>

<span data-ttu-id="a0b0f-108">Bu örnekte, `IEmployee` arabirim, bir okuma-yazma özelliğine, `Name` ve salt okunurdur bir özelliğe sahiptir `Counter`.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="a0b0f-109">Sınıf `Employee` `IEmployee` arabirimini uygular ve bu iki özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="a0b0f-110">Program yeni bir çalışanın adını ve geçerli çalışan sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="a0b0f-111">Özelliğin, üyenin bildirildiği arabirime başvuruda bulunduğu tam nitelikli adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="a0b0f-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a0b0f-112">For example:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="a0b0f-113">Buna [Açık arabirim uygulama](../interfaces/explicit-interface-implementation.md)adı verilir.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-113">This is called [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="a0b0f-114">Örneğin, sınıfı `Employee` iki arabirimi `ICitizen` ve `IEmployee` ve her iki arabirimde de `Name` özelliği varsa, açık arabirim üye uygulaması gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="a0b0f-115">Diğer bir deyişle, aşağıdaki özellik bildirimi:</span><span class="sxs-lookup"><span data-stu-id="a0b0f-115">That is, the following property declaration:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="a0b0f-116">, aşağıdaki bildirim sırasında `IEmployee` arabirimindeki `Name` özelliğini uygular:</span><span class="sxs-lookup"><span data-stu-id="a0b0f-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

<span data-ttu-id="a0b0f-117">`ICitizen` arabirimindeki `Name` özelliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-117">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="a0b0f-118">Örnek çıkış</span><span class="sxs-lookup"><span data-stu-id="a0b0f-118">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="a0b0f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0b0f-119">See also</span></span>

- [<span data-ttu-id="a0b0f-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a0b0f-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a0b0f-121">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="a0b0f-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="a0b0f-122">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a0b0f-122">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="a0b0f-123">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="a0b0f-123">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="a0b0f-124">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a0b0f-124">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="a0b0f-125">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a0b0f-125">Interfaces</span></span>](../interfaces/index.md)
