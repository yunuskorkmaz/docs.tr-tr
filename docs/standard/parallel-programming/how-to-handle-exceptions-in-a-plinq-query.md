---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: PLıNQ sorgusunda özel durumları Işleme'
title: 'Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 3699a913f227ac931dd40a29bfc28e7161b0db0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702021"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="ec2f5-103">Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="ec2f5-103">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="ec2f5-104">Bu konudaki ilk örnek, çalıştırıldığında PLıNQ sorgusundan oluşturulabilecek öğesinin nasıl işleneceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ec2f5-104">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="ec2f5-105">İkinci örnek, temsilcilerin içindeki try-catch bloklarının, özel durumun oluştuğu yere mümkün olduğunca yakın şekilde nasıl yerleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-105">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="ec2f5-106">Bu şekilde, bunları gerçekleştikleri anda yakalayabilir ve muhtemelen sorgu yürütmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-106">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="ec2f5-107">Özel durumların katılan iş parçacığına balon ekleme yapmasına izin verildiğinde, bir sorgu özel durum oluşturulduktan sonra bazı öğeleri işlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-107">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="ec2f5-108">PLıNQ, sıralı yürütmeye geri düştüğünde bazı durumlarda özel durum ortaya çıkabilir ve bir özel durum oluşur <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="ec2f5-108">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="ec2f5-109">Ayrıca, <xref:System.Threading.ThreadAbortException> s her zaman doğrudan yayılır.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-109">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="ec2f5-110">"Yalnızca kendi kodum" etkinleştirildiğinde, Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-110">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="ec2f5-111">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-111">This error is benign.</span></span> <span data-ttu-id="ec2f5-112">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-112">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="ec2f5-113">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel** altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-113">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="ec2f5-114">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-114">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="ec2f5-115">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="ec2f5-115">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="ec2f5-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec2f5-116">Example</span></span>

<span data-ttu-id="ec2f5-117">Bu örnek, her türlü oluşturulan öğeleri yakalamak için sorguyu yürüten kodun çevresine try-catch bloklarının nasıl yerleştirileceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ec2f5-117">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="ec2f5-118">Bu örnekte, özel durum oluşturulduktan sonra sorgu devam edemez.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-118">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="ec2f5-119">Uygulama kodunuzun özel durumu yakalamasına göre PLıNQ, sorguyu tüm iş parçacıklarında zaten durdurdu.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-119">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="ec2f5-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec2f5-120">Example</span></span>

<span data-ttu-id="ec2f5-121">Aşağıdaki örnek, bir özel durum yakalamak ve sorgu yürütmeye devam etmek için bir temsilciye bir try-catch bloğunun nasıl yerleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-121">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="ec2f5-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ec2f5-122">Compiling the Code</span></span>

- <span data-ttu-id="ec2f5-123">Bu örnekleri derlemek ve çalıştırmak için onları PLıNQ veri örneği örneğine kopyalayın ve Main 'den yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-123">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="ec2f5-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ec2f5-124">Robust Programming</span></span>

<span data-ttu-id="ec2f5-125">Programınızın durumunu bozmadığınız için nasıl işleneceğini bilmiyorsanız bir özel durum yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-125">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec2f5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec2f5-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="ec2f5-127">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ec2f5-127">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
