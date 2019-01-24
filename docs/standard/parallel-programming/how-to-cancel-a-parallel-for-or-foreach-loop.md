---
title: 'Nasıl yapılır: Bir Parallel.For veya ForEach döngüsünü iptal etme'
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
ms.openlocfilehash: 7cdb6e059fb1c7001bbe4da60e2936b1ad40cc1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618087"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="ab4a9-102">Nasıl yapılır: Bir Parallel.For veya ForEach döngüsünü iptal etme</span><span class="sxs-lookup"><span data-stu-id="ab4a9-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="ab4a9-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemleri iptal belirteçlerini kullanımıyla iptal etmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="ab4a9-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="ab4a9-104">Genel olarak, iptal etme hakkında daha fazla bilgi için bkz [iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="ab4a9-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="ab4a9-105">Paralel bir döngüde sağladığınız <xref:System.Threading.CancellationToken> yöntemine <xref:System.Threading.Tasks.ParallelOptions> parametresi ve ardından paralel çağrıyı bir try-catch bloğu içinde alın.</span><span class="sxs-lookup"><span data-stu-id="ab4a9-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab4a9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab4a9-106">Example</span></span>  
 <span data-ttu-id="ab4a9-107">Aşağıdaki örnek bir çağrı iptal etme gösterir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab4a9-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ab4a9-108">Aynı yaklaşımı uygulayabileceğiniz bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağırın.</span><span class="sxs-lookup"><span data-stu-id="ab4a9-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="ab4a9-109">Sinyalleri iptal belirteci aynı ise belirteç, belirtilen <xref:System.Threading.Tasks.ParallelOptions> paralel bir döngüden tek bir durum oluşturur sonra örnek <xref:System.OperationCanceledException> iptal seçeneğiyle ilgili.</span><span class="sxs-lookup"><span data-stu-id="ab4a9-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="ab4a9-110">Diğer bir belirteç iptali neden olursa, döngü oluşturur bir <xref:System.AggregateException> ile bir <xref:System.OperationCanceledException> olarak bir InnerException.</span><span class="sxs-lookup"><span data-stu-id="ab4a9-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4a9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab4a9-111">See also</span></span>

- [<span data-ttu-id="ab4a9-112">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="ab4a9-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="ab4a9-113">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ab4a9-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
