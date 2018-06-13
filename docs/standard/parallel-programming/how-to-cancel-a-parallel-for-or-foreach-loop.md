---
title: 'Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9b8b0864f3ed30c2ff03866abdb0d5d07991db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580396"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="e37dc-102">Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme</span><span class="sxs-lookup"><span data-stu-id="e37dc-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="e37dc-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemlerini desteklemek iptal iptal belirteçlerini kullanımı ile.</span><span class="sxs-lookup"><span data-stu-id="e37dc-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="e37dc-104">Genel olarak, iptal hakkında daha fazla bilgi için bkz [iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="e37dc-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="e37dc-105">Paralel bir döngüden sağladığınız <xref:System.Threading.CancellationToken> yöntemine <xref:System.Threading.Tasks.ParallelOptions> parametre ve bir try-catch bloğu içinde paralel çağrısı içine alın.</span><span class="sxs-lookup"><span data-stu-id="e37dc-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e37dc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e37dc-106">Example</span></span>  
 <span data-ttu-id="e37dc-107">Aşağıdaki örnek bir çağrı iptal etme gösterir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e37dc-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e37dc-108">Aynı yaklaşımı uygulayabilirsiniz bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağırın.</span><span class="sxs-lookup"><span data-stu-id="e37dc-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="e37dc-109">İptal sinyalleri belirteci aynı ise belirteç, belirtilen <xref:System.Threading.Tasks.ParallelOptions> paralel döngü tek bir özel durum oluşturacak sonra örnek <xref:System.OperationCanceledException> iptal üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e37dc-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="e37dc-110">Diğer bir belirteci iptal neden olursa, döngü özel durum oluşturacak bir <xref:System.AggregateException> ile bir <xref:System.OperationCanceledException> bir InnerException olarak.</span><span class="sxs-lookup"><span data-stu-id="e37dc-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37dc-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e37dc-111">See Also</span></span>  
 [<span data-ttu-id="e37dc-112">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="e37dc-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="e37dc-113">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e37dc-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
