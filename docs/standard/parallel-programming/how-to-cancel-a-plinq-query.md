---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: PLıNQ sorgusunu Iptal etme'
title: 'Nasıl yapılır: PLINQ Sorgusunu İptal Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: c81ea565beb7287389ea043fee5854eb592e5271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702196"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="1fd51-103">Nasıl yapılır: PLINQ Sorgusunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="1fd51-103">How to: Cancel a PLINQ Query</span></span>

<span data-ttu-id="1fd51-104">Aşağıdaki örneklerde PLıNQ sorgusunu iptal etmenin iki yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-104">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="1fd51-105">İlk örnek, çoğunlukla veri geçişi içeren bir sorgunun nasıl iptal edildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-105">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="1fd51-106">İkinci örnek, hesaplama açısından pahalı olan bir Kullanıcı işlevi içeren bir sorgunun nasıl iptal edildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-106">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="1fd51-107">"Yalnızca kendi kodum" etkinleştirildiğinde, Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1fd51-107">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="1fd51-108">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="1fd51-108">This error is benign.</span></span> <span data-ttu-id="1fd51-109">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fd51-109">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="1fd51-110">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel** altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-110">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="1fd51-111">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1fd51-112">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="1fd51-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="1fd51-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1fd51-113">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="1fd51-114">PLıNQ çerçevesi tek bir <xref:System.OperationCanceledException> içine değil <xref:System.AggregateException?displayProperty=nameWithType> ; <xref:System.OperationCanceledException> ayrı bir catch bloğunda işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-114">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="1fd51-115">Bir veya daha fazla kullanıcı temsilcisi bir Operationolaydexception (externalCT) oluşturursa (harici <xref:System.Threading.CancellationToken?displayProperty=nameWithType> ), ancak başka bir özel durum yoksa ve sorgu olarak tanımlanmışsa `AsParallel().WithCancellation(externalCT)` , PLINQ, <xref:System.OperationCanceledException> bir yerine tek bir (externalCT) verir <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1fd51-115">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fd51-116">Ancak, bir kullanıcı temsilcisi bir oluşturursa <xref:System.OperationCanceledException> ve başka bir temsilci başka bir özel durum türü oluşturursa, her iki özel durum da bir öğesine alınacaktır <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="1fd51-116">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="1fd51-117">İptal etme ile ilgili genel yönergeler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1fd51-117">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="1fd51-118">Kullanıcı temsilcisi iptali gerçekleştirmeniz durumunda, PLıNQ ile dış hakkında bilgilendirmeniz <xref:System.Threading.CancellationToken> ve bir <xref:System.OperationCanceledException> (externalCT) oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-118">If you perform user-delegate cancellation, you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="1fd51-119">İptal gerçekleşirse ve başka özel durumlar yoksa, yerine bir olarak işleyin <xref:System.OperationCanceledException> <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="1fd51-119">If cancellation occurs and no other exceptions are thrown, then handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="1fd51-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1fd51-120">Example</span></span>

<span data-ttu-id="1fd51-121">Aşağıdaki örnek, Kullanıcı kodunda hesaplama maliyetli bir işleviniz olduğunda iptalin nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-121">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="1fd51-122">Kullanıcı kodunda iptali işlerken, sorgu tanımında kullanmak zorunda değilsiniz <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> .</span><span class="sxs-lookup"><span data-stu-id="1fd51-122">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="1fd51-123">Ancak, <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu performansı üzerinde hiçbir etkisi olmadığından ve İptalin sorgu işleçleri ve Kullanıcı kodunuz tarafından işlenmesini sağladığından, kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-123">However, we recommended that you do use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="1fd51-124">Sistem yanıt verme işlemini sağlamak için, her milisaniyenin etrafında iptali denetlemeniz önerilir; Ancak, 10 milisaniyeye kadar olan tüm süreleri kabul edilebilir kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="1fd51-124">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="1fd51-125">Bu sıklık kodunuzun performansı üzerinde olumsuz bir etkiye sahip olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fd51-125">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="1fd51-126">Bir Numaralandırıcı atıldığı zaman, örneğin, sorgu sonuçları üzerinde yineleme yapan bir foreach (Visual Basic for each) döngüsünde kod kesildiğinde sorgu iptal edilir, ancak özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="1fd51-126">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is canceled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fd51-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fd51-127">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="1fd51-128">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1fd51-128">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
- [<span data-ttu-id="1fd51-129">Yönetilen Iş parçacıklarında iptal</span><span class="sxs-lookup"><span data-stu-id="1fd51-129">Cancellation in Managed Threads</span></span>](../threading/cancellation-in-managed-threads.md)
