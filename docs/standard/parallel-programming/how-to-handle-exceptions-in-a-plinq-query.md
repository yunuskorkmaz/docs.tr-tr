---
title: 'Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef107ae0dceb7ee937b21d65cba92cbcf6a9a96c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628994"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="08dd1-102">Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="08dd1-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="08dd1-103">Bu konudaki ilk örnek nasıl işleneceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> , durum konumundan bir PLINQ sorgusu yürütüldüğünde.</span><span class="sxs-lookup"><span data-stu-id="08dd1-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="08dd1-104">İkinci örnek, try-catch bloklarını temsilciler içinde özel durumun olduğu için mümkün olduğunca yakın yerleştirin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08dd1-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="08dd1-105">Oluşur ve büyük olasılıkla sorgu yürütmeye devam et hemen sonra bu şekilde, siz bunları yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="08dd1-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="08dd1-106">Ne zaman bir sorgu özel durum oluştuktan sonra bazı öğeleri işlemeye devam edebilir mümkündür özel durumları ayarlama geri katılan iş parçacığına Kabarcık halinde çıkmasına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="08dd1-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="08dd1-107">Bazı durumlarda PLINQ sıralı yürütme için geri döner ve özel bir durum oluştuğunda, özel durum doğrudan yayılır ve sarmalanmış değil bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="08dd1-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="08dd1-108">Ayrıca, <xref:System.Threading.ThreadAbortException>s her zaman yayılır doğrudan.</span><span class="sxs-lookup"><span data-stu-id="08dd1-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08dd1-109">"Yalnızca kendi kodum" etkin olduğunda, Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler</span><span class="sxs-lookup"><span data-stu-id="08dd1-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="08dd1-110">Bu hata zararsızdır.</span><span class="sxs-lookup"><span data-stu-id="08dd1-110">This error is benign.</span></span> <span data-ttu-id="08dd1-111">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın.</span><span class="sxs-lookup"><span data-stu-id="08dd1-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="08dd1-112">Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="08dd1-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="08dd1-113">Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="08dd1-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="08dd1-114">Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="08dd1-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08dd1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="08dd1-115">Example</span></span>  
 <span data-ttu-id="08dd1-116">Bu örnek nasıl herhangi yakalamak için sorgu yürütülen kod etrafında try-catch blokları yerleştirin gösterir <xref:System.AggregateException?displayProperty=nameWithType>oluşturulan s.</span><span class="sxs-lookup"><span data-stu-id="08dd1-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="08dd1-117">Bu örnekte, özel durum oluştuktan sonra sorgu devam edemiyor.</span><span class="sxs-lookup"><span data-stu-id="08dd1-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="08dd1-118">Zaman uygulama kodunuzun özel durumu yakalar, PLINQ sorguyu tüm iş parçacıkları üzerinde zaten durduruldu.</span><span class="sxs-lookup"><span data-stu-id="08dd1-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08dd1-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="08dd1-119">Example</span></span>  
 <span data-ttu-id="08dd1-120">Aşağıdaki örnek, bir özel durum yakalamak ve sorgu yürütme ile devam etmek mümkün kılmak için bir temsilci bir try-catch bloğu koymak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08dd1-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08dd1-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="08dd1-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="08dd1-122">Derleme ve bu örnekleri çalıştırmak için bunları PLINQ veri örneği örneği kopyalayın ve Main yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="08dd1-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="08dd1-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="08dd1-123">Robust Programming</span></span>  
 <span data-ttu-id="08dd1-124">Programınızın durumunu bozmadığından emin, ne yapılacağını bilmediği sürece bir özel durum yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="08dd1-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dd1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08dd1-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="08dd1-126">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="08dd1-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
