---
title: Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
ms.openlocfilehash: 6184e52c3f6e39e452331af27b83520e498062aa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289934"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="aeb68-102">Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme</span><span class="sxs-lookup"><span data-stu-id="aeb68-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="aeb68-103">Zaman uyumsuz bir işlemin sonuçlarının, işlem tamamlanana kadar durdurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aeb68-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="aeb68-104">Zaman uyumsuz bir işlemin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="aeb68-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="aeb68-105"><xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> Zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aeb68-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="aeb68-106">Bu yaklaşım, bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aeb68-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="aeb68-107">Zaman uyumsuz işlemin **bitiş**_OperationName_ yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="aeb68-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="aeb68-108">Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="aeb68-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="aeb68-109"><xref:System.Threading.WaitHandle>Zaman uyumsuz bir işlem tamamlanana kadar engellemek için bir veya daha fazla nesne kullanan uygulamalar genellikle **BEGIN**_OperationName_ yöntemini çağırır, işlem sonuçları olmadan yapılabilecek işleri gerçekleştirir ve ardından zaman uyumsuz işlemler tamamlanana kadar blok yapmaz.</span><span class="sxs-lookup"><span data-stu-id="aeb68-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="aeb68-110">Bir uygulama <xref:System.Threading.WaitHandle.WaitOne%2A> , yöntemini kullanarak yöntemlerinden birini çağırarak tek bir işlemde bloke edebilir <xref:System.IAsyncResult.AsyncWaitHandle%2A> .</span><span class="sxs-lookup"><span data-stu-id="aeb68-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="aeb68-111">Zaman uyumsuz işlemlerin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesneleri bir dizide depolayın ve yöntemlerinden birini çağırın <xref:System.Threading.WaitHandle.WaitAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="aeb68-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="aeb68-112">Zaman uyumsuz işlemler kümesinden herhangi birinin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesneleri bir dizide depolayın ve yöntemlerden birini çağırın <xref:System.Threading.WaitHandle.WaitAny%2A> .</span><span class="sxs-lookup"><span data-stu-id="aeb68-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb68-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeb68-113">Example</span></span>  
 <span data-ttu-id="aeb68-114">Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistem bilgilerini almak üzere DNS sınıfındaki zaman uyumsuz yöntemleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="aeb68-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="aeb68-115">Örnek, <xref:System.Threading.WaitHandle> zaman uyumsuz işlemle ilişkili öğesini kullanarak engellemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="aeb68-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="aeb68-116">`null` `Nothing` <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` Bu yaklaşım kullanıldığında gerekli olmadığından, ve parametreleri için (Visual Basic olarak) geçtiğini unutmayın `stateObject` .</span><span class="sxs-lookup"><span data-stu-id="aeb68-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="aeb68-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb68-117">See also</span></span>

- [<span data-ttu-id="aeb68-118">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="aeb68-118">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="aeb68-119">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aeb68-119">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
