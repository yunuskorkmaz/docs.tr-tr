---
title: 'Nasıl yapılır: PLINQ Sorgusunu İptal Etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 074371a929d5dd2cf0efb763ec45395a8dfd0432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584289"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="b7748-102">Nasıl yapılır: PLINQ Sorgusunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="b7748-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="b7748-103">Aşağıdaki örnekler bir PLINQ sorgusunu iptal etmek için iki yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7748-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="b7748-104">İlk örnek çoğunlukla veri geçişi oluşan bir sorguyu iptal gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7748-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="b7748-105">İkinci örnek pkı'ya pahalıdır kullanıcı işlevi içeren bir sorguyu iptal etme gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7748-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7748-106">"Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir</span><span class="sxs-lookup"><span data-stu-id="b7748-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="b7748-107">Bu hata zararsız kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="b7748-107">This error is benign.</span></span> <span data-ttu-id="b7748-108">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın.</span><span class="sxs-lookup"><span data-stu-id="b7748-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="b7748-109">Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="b7748-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="b7748-110">Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b7748-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="b7748-111">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="b7748-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7748-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7748-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="b7748-113">Tek bir PLINQ framework döndürülmez <xref:System.OperationCanceledException> içine bir <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> ayrı catch bloğunda ele alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7748-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="b7748-114">Bir veya daha fazla kullanıcı temsilcileri bir OperationCanceledException(externalCT) oluşturursa (bir dış kullanarak <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ancak başka bir özel durum ve sorgu olarak tanımlanmıştı `AsParallel().WithCancellation(externalCT)`, tek bir PLINQ verecek sonra <xref:System.OperationCanceledException> (externalCT) yerine bir <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7748-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7748-115">Ancak, bir kullanıcı temsilci döndürürse bir <xref:System.OperationCanceledException>ve başka bir özel durum türü başka bir temsilci oluşturur ve ardından her iki özel durumlar içine alınacak bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="b7748-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="b7748-116">İptal genel yönergeler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b7748-116">The general guidance on cancellation is as follows:</span></span>  
  
1.  <span data-ttu-id="b7748-117">Kullanıcı temsilci iptal gerçekleştirirseniz PLINQ dış hakkında bilgilendirmek <xref:System.Threading.CancellationToken> ve throw bir <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="b7748-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2.  <span data-ttu-id="b7748-118">İptal gerçekleşir ve başka bir özel durum, daha sonra işlemesi gereken bir <xref:System.OperationCanceledException> yerine bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="b7748-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7748-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7748-119">Example</span></span>  
 <span data-ttu-id="b7748-120">Aşağıdaki örnekte nasıl pkı'ya pahalı bir işlev içinde kullanıcı kodu varsa, iptal işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7748-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="b7748-121">Kullanıcı kodu iptal uyguluyorsanız kullanmak gerekmez <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu tanımı içinde.</span><span class="sxs-lookup"><span data-stu-id="b7748-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="b7748-122">Ancak, çünkü bunu yapmanızı öneririz <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu performansı üzerinde hiçbir etkisi olmaz ve sorgu işleçleri ve kullanıcı kodu tarafından işlenecek iptal sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7748-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="b7748-123">Sistem Yanıtlama Hızı emin olmak için İptal mili saniye başına bir kez çözmek için denetlemenizi öneririz; Bununla birlikte, 10 milisaniye kadar herhangi bir süre kabul edilebilir kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b7748-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="b7748-124">Bu sıklık olumsuz etkiler, kodun performans üzerinde yok.</span><span class="sxs-lookup"><span data-stu-id="b7748-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="b7748-125">Bir numaralandırıcı olduğunda, örneğin, kod sorgu sonuçları yineleme bir (her biri için Visual Basic) foreach döngüsü dışında keser sonra sorgu iptal edildi, ancak hiçbir özel durum.</span><span class="sxs-lookup"><span data-stu-id="b7748-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7748-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7748-126">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="b7748-127">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b7748-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="b7748-128">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="b7748-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
