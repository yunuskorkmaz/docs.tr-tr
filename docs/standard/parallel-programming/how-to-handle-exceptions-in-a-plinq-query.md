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
ms.openlocfilehash: 162ef3849f025cae9196c2f595634f82cfc782df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580750"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="1d5e5-102">Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="1d5e5-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="1d5e5-103">Bu konudaki ilk örnek nasıl işleneceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> , durum ile bir PLINQ sorgusu yürütüldüğünde.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="1d5e5-104">İkinci örnek try-catch bloklarını temsilciler içinde özel durumun nerede için mümkün olduğunca yakın put gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="1d5e5-105">Oluşur ve büyük olasılıkla sorgu yürütme devam hemen bu şekilde, siz bunları yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="1d5e5-106">Özel durum oluşturulduktan sonra bazı öğeleri işlemek bir sorgu devam edebilir mümkündür ne zaman özel durumlar oluşturan geri katılma akışa Kabarcık izin verilir.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="1d5e5-107">Bazı durumlarda PLINQ sıralı yürütme geri döner ve bir özel durum gerçekleştiğinde, özel durum doğrudan yayılan ve sarmalanmış olmayan bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="1d5e5-108">Ayrıca, <xref:System.Threading.ThreadAbortException>s her zaman yayılır doğrudan.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d5e5-109">"Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir</span><span class="sxs-lookup"><span data-stu-id="1d5e5-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="1d5e5-110">Bu hata zararsız kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-110">This error is benign.</span></span> <span data-ttu-id="1d5e5-111">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="1d5e5-112">Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="1d5e5-113">Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1d5e5-114">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="1d5e5-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d5e5-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d5e5-115">Example</span></span>  
 <span data-ttu-id="1d5e5-116">Bu örnek herhangi yakalamak üzere Sorguyu yürüten kod geçici try-catch bloklarını put gösterilmektedir <xref:System.AggregateException?displayProperty=nameWithType>oluşturulan s.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="1d5e5-117">Özel durum oluşturulduktan sonra bu örnekte, sorgu devam edemiyor.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="1d5e5-118">Özel durum, uygulama kodunuzun yakalar zamanına göre PLINQ sorgu tüm iş parçacıklarında zaten durduruldu.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d5e5-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d5e5-119">Example</span></span>  
 <span data-ttu-id="1d5e5-120">Aşağıdaki örnek, bir temsilci bir özel durum yakalama ve sorgu yürütmesi ile devam etmek mümkün kılmak için bir try-catch bloğu koymak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d5e5-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1d5e5-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1d5e5-122">Derlemek ve bu örnekleri çalıştırmak için bunları PLINQ veri örneği örneği kopyalayın ve Main yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1d5e5-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1d5e5-123">Robust Programming</span></span>  
 <span data-ttu-id="1d5e5-124">Böylece programınızı durumu bozuk olmayan işlemek nasıl bilmiyorsanız bir özel durum catch değil.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5e5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d5e5-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="1d5e5-126">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1d5e5-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
