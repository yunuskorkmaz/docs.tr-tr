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
ms.openlocfilehash: 67f1f91f235cc88deaa97d412f368819ae0a8cda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134240"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="fe858-102">Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme</span><span class="sxs-lookup"><span data-stu-id="fe858-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="fe858-103">Ve <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemler iptal belirteçleri kullanarak iptali destekler.</span><span class="sxs-lookup"><span data-stu-id="fe858-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="fe858-104">Genel olarak iptal hakkında daha fazla bilgi için [İptal'e](../../../docs/standard/threading/cancellation-in-managed-threads.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fe858-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="fe858-105">Paralel bir döngüde, <xref:System.Threading.CancellationToken> <xref:System.Threading.Tasks.ParallelOptions> yönteme parametreyi sağlarsınız ve paralel aramayı try-catch bloğuna içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe858-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe858-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe858-106">Example</span></span>  
 <span data-ttu-id="fe858-107">Aşağıdaki örnekte, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>'ye yapılan bir çağrının nasıl iptal edilebildiğini gösterir</span><span class="sxs-lookup"><span data-stu-id="fe858-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe858-108">Aynı yaklaşımı bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağrıya da uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe858-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="fe858-109">İptal sinyali veren <xref:System.Threading.Tasks.ParallelOptions> belirteç, örneğin belirtilen belirteçle aynıysa, paralel döngü <xref:System.OperationCanceledException> iptal de tek bir belirtme atar.</span><span class="sxs-lookup"><span data-stu-id="fe858-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="fe858-110">Başka bir belirteç iptale neden <xref:System.AggregateException> olursa, <xref:System.OperationCanceledException> döngü bir InnerException olarak bir atacaktır.</span><span class="sxs-lookup"><span data-stu-id="fe858-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe858-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe858-111">See also</span></span>

- [<span data-ttu-id="fe858-112">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="fe858-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="fe858-113">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="fe858-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
