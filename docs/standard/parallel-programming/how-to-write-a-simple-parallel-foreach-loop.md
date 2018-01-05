---
title: "Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bb628c0de1f0e4452ae13b5f5ee392084118bea5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="555b1-102">Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma</span><span class="sxs-lookup"><span data-stu-id="555b1-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="555b1-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veri paralelliği herhangi etkinleştirmek için döngü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="555b1-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="555b1-104">Bu belge lambda ifadeleri temsilciler PLINQ'te tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="555b1-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="555b1-105">C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="555b1-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="555b1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="555b1-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="555b1-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü çalışır gibi bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü.</span><span class="sxs-lookup"><span data-stu-id="555b1-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="555b1-108">Kaynak koleksiyonu bölümlenmiş ve sistem ortamına bağlı birden çok iş parçacığı üzerinde çalışma zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="555b1-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="555b1-109">Daha fazla işlemci sistemdeki paralel yöntemi daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="555b1-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="555b1-110">Bazı kaynak koleksiyonlar için sıralı döngü hızlı, kaynak ve gerçekleştirilen iş türünü boyutuna bağlı olarak olabilir.</span><span class="sxs-lookup"><span data-stu-id="555b1-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="555b1-111">Performansı hakkında daha fazla bilgi için bkz: [veri ve görev Paralelliğinde olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="555b1-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="555b1-112">Paralel döngüler hakkında daha fazla bilgi için bkz: [nasıl yapılır: basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="555b1-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="555b1-113">Kullanılacak <xref:System.Threading.Tasks.Parallel.ForEach%2A> genel olmayan koleksiyonu ile kullandığınız <xref:System.Linq.Enumerable.Cast%2A> genişletme yöntemi aşağıdaki örnekte gösterildiği gibi genel bir koleksiyon için koleksiyon dönüştürmek için:</span><span class="sxs-lookup"><span data-stu-id="555b1-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="555b1-114">Paralel LINQ (PLINQ) işlenmesini paralel hale kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veri kaynakları.</span><span class="sxs-lookup"><span data-stu-id="555b1-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="555b1-115">PLINQ döngü davranışı ifade etmek için bildirim temelli sorgu söz dizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="555b1-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="555b1-116">Daha fazla bilgi için bkz: [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="555b1-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="555b1-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="555b1-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="555b1-118">Bu kodu kopyalayıp bir [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 konsol uygulama projesi.</span><span class="sxs-lookup"><span data-stu-id="555b1-118">Copy and paste this code into a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="555b1-119">System.Drawing.dll bir başvuru ekleyin</span><span class="sxs-lookup"><span data-stu-id="555b1-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="555b1-120">F5 tuşuna basın</span><span class="sxs-lookup"><span data-stu-id="555b1-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555b1-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="555b1-121">See Also</span></span>  
 [<span data-ttu-id="555b1-122">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="555b1-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="555b1-123">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="555b1-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="555b1-124">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="555b1-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
