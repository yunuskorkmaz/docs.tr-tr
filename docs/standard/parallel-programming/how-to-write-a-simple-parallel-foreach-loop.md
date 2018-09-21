---
title: ForEach kullanarak basit bir paralel programı yazma
ms.date: 09/12/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a9a2ca668ee2cccc2211250bc1c7c49c87f38c2
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492830"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="f9572-102">Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma</span><span class="sxs-lookup"><span data-stu-id="f9572-102">How to: Write a Simple Parallel.ForEach Loop</span></span>

<span data-ttu-id="f9572-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veri paralelliği herhangi birini etkinleştirmek için döngü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="f9572-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="f9572-104">Bu belgede lambda ifadeleri PLINQ'te temsilciler tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9572-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="f9572-105">C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="f9572-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="f9572-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9572-106">Example</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="f9572-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü çalışır gibi bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü.</span><span class="sxs-lookup"><span data-stu-id="f9572-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="f9572-108">Kaynak koleksiyonu bölümlenen ve sistem ortama bağlı birden çok iş parçacığında iş zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="f9572-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="f9572-109">Daha fazla işlemci sistem üzerinde paralel yöntemi daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="f9572-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="f9572-110">Bazı kaynak koleksiyonları için hızlı, kaynak ve gerçekleştirilmekte olan iş türünü boyutuna bağlı olarak sıralı bir döngü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9572-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="f9572-111">Performans hakkında daha fazla bilgi için bkz: [veri ve görev Paralelliğinde olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="f9572-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>

<span data-ttu-id="f9572-112">Paralel döngüler hakkında daha fazla bilgi için bkz: [nasıl yapılır: basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="f9572-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="f9572-113">Kullanılacak <xref:System.Threading.Tasks.Parallel.ForEach%2A> kullanabileceğiniz bir genel olmayan koleksiyonu ile <xref:System.Linq.Enumerable.Cast%2A> genişletme yöntemi, aşağıdaki örnekte gösterildiği gibi genel bir koleksiyon için koleksiyon dönüştürmek için:</span><span class="sxs-lookup"><span data-stu-id="f9572-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="f9572-114">Paralel LINQ (PLINQ) işlenmesini paralel hale getirmek için de kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veri kaynakları.</span><span class="sxs-lookup"><span data-stu-id="f9572-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="f9572-115">PLINQ, döngü davranışı ifade etmek için bildirim temelli bir sorgu söz dizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9572-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="f9572-116">Daha fazla bilgi için [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f9572-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="f9572-117">Derleme ve kod çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f9572-117">Compile and run the code</span></span>

- <span data-ttu-id="f9572-118">Bu kod Visual Studio'ya kopyalayıp **konsol uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="f9572-118">Copy and paste this code into a Visual Studio **Console App** project.</span></span>

- <span data-ttu-id="f9572-119">System.Drawing.dll bir başvuru ekleyin</span><span class="sxs-lookup"><span data-stu-id="f9572-119">Add a reference to System.Drawing.dll</span></span>

- <span data-ttu-id="f9572-120">Tuşuna **F5**</span><span class="sxs-lookup"><span data-stu-id="f9572-120">Press **F5**</span></span>

## <a name="see-also"></a><span data-ttu-id="f9572-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9572-121">See also</span></span>

- [<span data-ttu-id="f9572-122">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="f9572-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="f9572-123">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="f9572-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="f9572-124">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f9572-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
