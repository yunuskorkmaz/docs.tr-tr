---
title: 'Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0192e12c86b21eb126293bbd220e093b334768b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47456005"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="833a4-102">Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma</span><span class="sxs-lookup"><span data-stu-id="833a4-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="833a4-103">Bu örnekte, işlemleri kullanarak paralel hale getirmek gösterilmektedir <xref:System.Threading.Tasks.Parallel.Invoke%2A> görev paralel Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="833a4-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="833a4-104">Üç işlemi bir paylaşılan veri kaynağı üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="833a4-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="833a4-105">İşlemlerden hiçbiri kaynak değiştirdiğinden, bunlar basit bir şekilde paralel olarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="833a4-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="833a4-106">TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="833a4-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="833a4-107">C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="833a4-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="833a4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="833a4-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="833a4-109">İle dikkat <xref:System.Threading.Tasks.Parallel.Invoke%2A>, eşzamanlı olarak çalıştırmak istediğiniz eylemleri yalnızca express ve çalışma zamanı zamanlama ayrıntıları, ana bilgisayarda çekirdek sayısı için otomatik olarak ölçeklendirme dahil olmak üzere tüm iş parçacığı işler.</span><span class="sxs-lookup"><span data-stu-id="833a4-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="833a4-110">Bu örnekte, işlemler, veri parallelizes.</span><span class="sxs-lookup"><span data-stu-id="833a4-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="833a4-111">Alternatif bir yaklaşım PLINQ kullanarak LINQ sorgularını paralel hale getirmek ve sorguları sırayla çalışır.</span><span class="sxs-lookup"><span data-stu-id="833a4-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="833a4-112">Alternatif olarak, PLINQ kullanarak verileri paralel.</span><span class="sxs-lookup"><span data-stu-id="833a4-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="833a4-113">Başka bir sorgu hem görevleri paralel hale getirmek için bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="833a4-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="833a4-114">Ortaya çıkan performans nispeten daha az sayıda işlemcilere sahip ana bilgisayarlara ek yükü azaltabilir olsa da, birçok işlemcilere sahip bilgisayarlarda çok daha iyi ölçekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="833a4-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="833a4-115">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="833a4-115">Compile the Code</span></span>

<span data-ttu-id="833a4-116">Örneğin tamamını Microsoft Visual Studio projesi ve tuşuna yapıştırın **F5**.</span><span class="sxs-lookup"><span data-stu-id="833a4-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="833a4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="833a4-117">See also</span></span>

- [<span data-ttu-id="833a4-118">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="833a4-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="833a4-119">Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme</span><span class="sxs-lookup"><span data-stu-id="833a4-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="833a4-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="833a4-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
