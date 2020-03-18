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
ms.openlocfilehash: 272f25d62cb63c60209be3bc54dc5e76fb30df54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134224"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="1c474-102">Nasıl yapılır: PLINQ Sorgusunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="1c474-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="1c474-103">Aşağıdaki örnekler, plinq sorgusunu iptal etmenin iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c474-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="1c474-104">İlk örnek, çoğunlukla veri geçişinden oluşan bir sorgunun nasıl iptal edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c474-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="1c474-105">İkinci örnek, hesaplama olarak pahalı bir kullanıcı işlevi içeren bir sorguyu nasıl iptal ediletilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c474-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="1c474-106">"Yalnızca Kodum" etkinleştirildiğinde, Visual Studio özel durumu atan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c474-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="1c474-107">Bu hata iyi huylu.</span><span class="sxs-lookup"><span data-stu-id="1c474-107">This error is benign.</span></span> <span data-ttu-id="1c474-108">Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c474-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="1c474-109">Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1c474-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="1c474-110">Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1c474-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1c474-111">Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1c474-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="1c474-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c474-112">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="1c474-113">PLINQ çerçevesi tek <xref:System.OperationCanceledException> bir rulo <xref:System.AggregateException?displayProperty=nameWithType>yok; ayrı <xref:System.OperationCanceledException> bir yakalama bloğunda ele alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c474-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="1c474-114">Bir veya daha fazla kullanıcı temsilcisi bir OperationCanceledException (harici CT) atar ama başka <xref:System.Threading.CancellationToken?displayProperty=nameWithType>bir özel `AsParallel().WithCancellation(externalCT)`durum, ve sorgu olarak <xref:System.OperationCanceledException> tanımlanmıştır , sonra <xref:System.AggregateException?displayProperty=nameWithType>PLINQ yerine tek bir (hariciCT) verecektir .</span><span class="sxs-lookup"><span data-stu-id="1c474-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c474-115">Ancak, bir kullanıcı temsilcisi <xref:System.OperationCanceledException>bir , ve başka bir temsilci başka bir özel durum <xref:System.AggregateException>türü atar, sonra her iki özel durum bir .</span><span class="sxs-lookup"><span data-stu-id="1c474-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="1c474-116">İptal ile ilgili genel kılavuz aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1c474-116">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="1c474-117">Kullanıcı temsilcisi iptali yaparsanız PLINQ'u <xref:System.Threading.CancellationToken> harici hakkında <xref:System.OperationCanceledException>bilgilendirmeli ve bir (harici CT) atmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1c474-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="1c474-118">İptal oluşursa ve başka bir özel durum atılırsa, <xref:System.AggregateException>bir yerine bir <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="1c474-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="1c474-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c474-119">Example</span></span>

<span data-ttu-id="1c474-120">Aşağıdaki örnek, kullanıcı kodunda hesaplama açısından pahalı bir işleviniz olduğunda iptalin nasıl işleyeceğinigösterir.</span><span class="sxs-lookup"><span data-stu-id="1c474-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="1c474-121">Kullanıcı kodundaki iptali işlediğinizde, sorgu <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> tanımında kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1c474-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="1c474-122">Ancak, sorgu performansı üzerinde <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> hiçbir etkisi olmadığı ve iptalin sorgu operatörleri ve kullanıcı kodunuz tarafından gerçekleştirilmesini sağladığı için bunu yapmanızı tavsiye ettik.</span><span class="sxs-lookup"><span data-stu-id="1c474-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="1c474-123">Sistem duyarlılığını sağlamak için, iptali milisaniyede bir kez kontrol etmenizi öneririz; ancak, 10 milisaniyeye kadar olan herhangi bir dönem kabul edilebilir kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="1c474-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="1c474-124">Bu sıklığın kodunuzu performansında olumsuz bir etkisi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c474-124">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="1c474-125">Bir enumerator atıldığında, örneğin sorgu sonuçları üzerinde yineleme yapan bir foreach (Visual Basic'teki her biri için) döngüsünden kod çıktığında, sorgu iptal edilir, ancak özel durum atılmaz.</span><span class="sxs-lookup"><span data-stu-id="1c474-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c474-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c474-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="1c474-127">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1c474-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="1c474-128">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="1c474-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
