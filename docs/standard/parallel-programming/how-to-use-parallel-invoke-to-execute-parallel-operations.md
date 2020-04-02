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
ms.openlocfilehash: 7189c478e132a41971a364b833f0fabda6ff84d4
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588407"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="ebdb4-102">Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma</span><span class="sxs-lookup"><span data-stu-id="ebdb4-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="ebdb4-103">Bu örnek, Görev Paralel Kitaplığı'nda kullanarak <xref:System.Threading.Tasks.Parallel.Invoke%2A> işlemleri nasıl paralelleştireceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="ebdb4-104">Paylaşılan bir veri kaynağında üç işlem gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="ebdb4-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="ebdb4-106">TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="ebdb4-107">C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="ebdb4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebdb4-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="ebdb4-109"><xref:System.Threading.Tasks.Parallel.Invoke%2A>'ile, yalnızca aynı anda çalıştırmak istediğiniz eylemleri ifade eve ve çalışma zamanı ana bilgisayardaki çekirdek sayısına otomatik olarak ölçekleme de dahil olmak üzere tüm iş parçacığı zamanlama ayrıntılarını işler.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="ebdb4-110">Bu örnek, verileri değil, işlemleri paralelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="ebdb4-111">Alternatif bir yaklaşım olarak, PLINQ kullanarak LINQ sorgularını paralelleştirebilir ve sorguları sırayla çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="ebdb4-112">Alternatif olarak, PLINQ kullanarak verileri paralelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="ebdb4-113">Başka bir seçenek sorguları ve görevleri paralelleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="ebdb4-114">Ortaya çıkan genel gider, nispeten az işlemciye sahip ana bilgisayardaki performansı düşürebilir, ancak birçok işlemciye sahip bilgisayarlarda çok daha iyi ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="ebdb4-115">Kodu Derleme</span><span class="sxs-lookup"><span data-stu-id="ebdb4-115">Compile the Code</span></span>

<span data-ttu-id="ebdb4-116">Tüm örneği kopyalayıp bir Microsoft Visual Studio projesine yapıştırın ve **F5 tuşuna**basın.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebdb4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-117">See also</span></span>

- [<span data-ttu-id="ebdb4-118">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="ebdb4-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="ebdb4-119">Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme</span><span class="sxs-lookup"><span data-stu-id="ebdb4-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="ebdb4-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ebdb4-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
