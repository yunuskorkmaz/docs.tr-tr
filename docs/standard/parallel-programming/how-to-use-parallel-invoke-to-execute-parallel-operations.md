---
title: "Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma"
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
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a51f180a394c1baa2ecb0620279ea15c62e1edc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="bb67f-102">Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma</span><span class="sxs-lookup"><span data-stu-id="bb67f-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>
<span data-ttu-id="bb67f-103">Bu örnek kullanarak işlemleri paralel hale gösterilmiştir <xref:System.Threading.Tasks.Parallel.Invoke%2A> görev paralel Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="bb67f-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="bb67f-104">Üç işlemleri bir paylaşılan veri kaynağı üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bb67f-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="bb67f-105">İşlemlerin hiçbiri kaynak değiştirdiğinden, bunlar kolay bir şekilde paralel olarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb67f-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb67f-106">TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb67f-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="bb67f-107">C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="bb67f-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb67f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb67f-108">Example</span></span>  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 <span data-ttu-id="bb67f-109">İle unutmayın <xref:System.Threading.Tasks.Parallel.Invoke%2A>, aynı anda çalıştırmak istediğiniz hangi eylemleri yalnızca express ve çalışma zamanı zamanlama ayrıntıları, ana bilgisayarda çekirdek sayısı için otomatik olarak ölçeklendirme dahil olmak üzere tüm iş parçacığı işler.</span><span class="sxs-lookup"><span data-stu-id="bb67f-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>  
  
 <span data-ttu-id="bb67f-110">Bu örnek veri işlemleri parallelizes.</span><span class="sxs-lookup"><span data-stu-id="bb67f-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="bb67f-111">Alternatif bir yaklaşım PLINQ kullanarak LINQ sorgularını paralel hale ve sorguları sırayla çalışır.</span><span class="sxs-lookup"><span data-stu-id="bb67f-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="bb67f-112">Alternatif olarak, verileri PLINQ kullanarak paralel hale.</span><span class="sxs-lookup"><span data-stu-id="bb67f-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="bb67f-113">Sorgular ve görevleri paralel hale başka bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="bb67f-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="bb67f-114">Elde edilen performansını nispeten az işlemci ile ana bilgisayarlara ek yükü azaltabilir rağmen birçok işlemcilere sahip bilgisayarlarda daha iyi ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="bb67f-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb67f-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bb67f-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="bb67f-116">Kopyalama, tüm örnek bir Microsoft Visual Studio 2010 projeye yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bb67f-116">Copy and paste the entire example into a Microsoft Visual Studio 2010 project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb67f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb67f-117">See Also</span></span>  
 [<span data-ttu-id="bb67f-118">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="bb67f-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="bb67f-119">Nasıl yapılır: bir görevi ve alt öğelerini iptal etme</span><span class="sxs-lookup"><span data-stu-id="bb67f-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [<span data-ttu-id="bb67f-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="bb67f-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
