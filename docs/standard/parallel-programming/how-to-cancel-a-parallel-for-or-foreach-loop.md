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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134240"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="1241d-102">Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme</span><span class="sxs-lookup"><span data-stu-id="1241d-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="1241d-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemleri, iptal belirteçleri kullanılarak iptali destekler.</span><span class="sxs-lookup"><span data-stu-id="1241d-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="1241d-104">Genel olarak iptal hakkında daha fazla bilgi için bkz. [iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="1241d-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="1241d-105">Paralel bir döngüde, <xref:System.Threading.Tasks.ParallelOptions> parametresindeki yöntemine <xref:System.Threading.CancellationToken> sağlarsınız ve sonra bir try-catch bloğunda paralel çağrıyı içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="1241d-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1241d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1241d-106">Example</span></span>  
 <span data-ttu-id="1241d-107">Aşağıdaki örnek <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>çağrısının nasıl iptal edildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1241d-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1241d-108"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağrısına aynı yaklaşımı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1241d-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="1241d-109">İptali işaret eden belirteç <xref:System.Threading.Tasks.ParallelOptions> örneğinde belirtilen belirteçtir, paralel döngü iptal durumunda tek bir <xref:System.OperationCanceledException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1241d-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="1241d-110">Başka bir belirteç iptaline neden olursa, döngü bir InnerException olarak <xref:System.OperationCanceledException> bir <xref:System.AggregateException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1241d-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1241d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1241d-111">See also</span></span>

- [<span data-ttu-id="1241d-112">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="1241d-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="1241d-113">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1241d-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
