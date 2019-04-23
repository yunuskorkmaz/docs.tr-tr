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
ms.openlocfilehash: 80dc5f72bac436d4935c1697347d588b1a302f86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305344"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="8f67d-102">Nasıl yapılır: PLINQ Sorgusunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="8f67d-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="8f67d-103">Aşağıdaki örnekler, PLINQ sorgusunu iptal etme için iki yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f67d-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="8f67d-104">İlk örnek, çoğunlukla veri geçişini oluşan bir sorguyu iptal gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f67d-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="8f67d-105">İkinci örnek, hesaplama açısından pahalıdır bir kullanıcı işlevi içeren bir sorguyu iptal gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f67d-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f67d-106">"Yalnızca kendi kodum" etkin olduğunda, Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler</span><span class="sxs-lookup"><span data-stu-id="8f67d-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="8f67d-107">Bu hata zararsızdır.</span><span class="sxs-lookup"><span data-stu-id="8f67d-107">This error is benign.</span></span> <span data-ttu-id="8f67d-108">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın.</span><span class="sxs-lookup"><span data-stu-id="8f67d-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="8f67d-109">Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="8f67d-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="8f67d-110">Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8f67d-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="8f67d-111">Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="8f67d-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f67d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f67d-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="8f67d-113">Tek bir PLINQ framework dönmez <xref:System.OperationCanceledException> içine bir <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> ayrı bir catch bloğu içinde işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f67d-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="8f67d-114">Bir veya daha fazla kullanıcı temsilcileri bir OperationCanceledException(externalCT) oluşturursa (Dış kullanarak <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) başka bir özel durum ve sorgu olarak tanımlandı, ancak `AsParallel().WithCancellation(externalCT)`, tek bir PLINQ verecek sonra <xref:System.OperationCanceledException> (externalCT) yerine <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f67d-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f67d-115">Bir kullanıcı temsilcisi ancak oluşturur bir <xref:System.OperationCanceledException>ve başka bir özel durum türü başka bir temsilci oluşturur ve ardından her iki özel durum halinde alınacak bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="8f67d-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="8f67d-116">İptal seçeneğiyle ilgili genel kılavuz aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8f67d-116">The general guidance on cancellation is as follows:</span></span>  
  
1. <span data-ttu-id="8f67d-117">Kullanıcı Temsilcisi iptal gerçekleştirirseniz PLINQ dış hakkında bilgilendirmek <xref:System.Threading.CancellationToken> ve throw bir <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="8f67d-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2. <span data-ttu-id="8f67d-118">İptal gerçekleşirse ve başka bir özel durum oluşturulur, ardından, işleyeceğini bir <xref:System.OperationCanceledException> yerine <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="8f67d-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f67d-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f67d-119">Example</span></span>  
 <span data-ttu-id="8f67d-120">Aşağıdaki örnek, kullanıcı kodunda hesaplama açısından pahalı bir işlev olduğunda iptal nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f67d-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="8f67d-121">Kullanıcı kodunda iptal işlediğinizde kullanın gerekmez <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu tanımı içinde.</span><span class="sxs-lookup"><span data-stu-id="8f67d-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="8f67d-122">Ancak, çünkü bunu yapmanızı öneririz <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu performansı üzerinde hiçbir etkisi yoktur ve sorgu işleçleri ve kullanıcı kod tarafından işlenecek iptal sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f67d-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="8f67d-123">Sistem yanıt hızını emin olmak için İptal milisaniyelik başına bir kez etrafında kontrol etmenizi öneririz; Ancak, herhangi bir süre 10 milisaniyeden kadar kabul edilebilir kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8f67d-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="8f67d-124">Bu sıklığı kodunuzun performansı üzerinde olumsuz bir etkiye sahip olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f67d-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="8f67d-125">Bir numaralandırıcı, örneğin, kod, sorgu sonuçları üzerinde yineleme (For Each Visual Basic'te) foreach döngüsünün dışında keser sonra sorgu iptal edildi, ancak hiçbir özel durum.</span><span class="sxs-lookup"><span data-stu-id="8f67d-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f67d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f67d-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="8f67d-127">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="8f67d-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="8f67d-128">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="8f67d-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
