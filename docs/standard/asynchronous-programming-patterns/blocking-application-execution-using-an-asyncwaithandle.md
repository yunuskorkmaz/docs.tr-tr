---
title: "Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="1cab4-102">Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme</span><span class="sxs-lookup"><span data-stu-id="1cab4-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="1cab4-103">İşlemi tamamlanana kadar diğer iş zaman uyumsuz bir işlem sonuçları için beklenirken yapmak için devam edemiyor uygulamaları engellemelidir.</span><span class="sxs-lookup"><span data-stu-id="1cab4-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="1cab4-104">Bir zaman uyumsuz bir işlemin tamamlanması beklenirken, uygulamanın ana iş parçacığı engellemek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="1cab4-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="1cab4-105">Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak** *OperationName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1cab4-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="1cab4-106">Bu yaklaşım, bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1cab4-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="1cab4-107">Zaman uyumsuz işlem çağrısı **son** *OperationName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1cab4-107">Call the asynchronous operation's **End** *OperationName* method.</span></span> <span data-ttu-id="1cab4-108">Bu yaklaşım gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırarak uygulamanın yürütülmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1cab4-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="1cab4-109">Bir veya daha fazla kullanan uygulamaları <xref:System.Threading.WaitHandle> zaman uyumsuz bir işlem tamamlanana kadar engellemek için nesneleri genellikle çağıracaktır **başlamak** *OperationName* yöntemi yapılabilir herhangi bir iş gerçekleştirin işlem, ardından zaman uyumsuz işlemleri kadar blok sonuçlarını olmadan tamamlar.</span><span class="sxs-lookup"><span data-stu-id="1cab4-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="1cab4-110">Bir uygulama üzerinde tek bir işlemi birini çağırarak engelleyebilirsiniz <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemlerini kullanarak <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span><span class="sxs-lookup"><span data-stu-id="1cab4-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="1cab4-111">Bir dizi tamamlamak için zaman uyumsuz işlemleri için beklenirken engellemek için ilişkili depolama <xref:System.IAsyncResult.AsyncWaitHandle%2A> bir dizi ve, çağrı nesneleri <xref:System.Threading.WaitHandle.WaitAll%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="1cab4-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="1cab4-112">Bir dizi tamamlamak için zaman uyumsuz işlemleri herhangi biri için beklenirken engellemek için ilişkili depolama <xref:System.IAsyncResult.AsyncWaitHandle%2A> bir dizi ve, çağrı nesneleri <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="1cab4-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cab4-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cab4-113">Example</span></span>  
 <span data-ttu-id="1cab4-114">Aşağıdaki kod örneğinde, kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistemi bilgileri almak için DNS sınıfında zaman uyumsuz yöntemleri kullanarak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1cab4-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="1cab4-115">Örnek kullanarak engelleme gösterir <xref:System.Threading.WaitHandle> zaman uyumsuz işlemle ilişkili.</span><span class="sxs-lookup"><span data-stu-id="1cab4-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="1cab4-116">Unutmayın `null` (`Nothing` Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` ve `stateObject` parametreleri bunlar bu yaklaşımı kullanarak, gerekli olmadığından.</span><span class="sxs-lookup"><span data-stu-id="1cab4-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1cab4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cab4-117">See Also</span></span>  
 [<span data-ttu-id="1cab4-118">Olay tabanlı zaman uyumsuz desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="1cab4-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="1cab4-119">Olay tabanlı zaman uyumsuz desene genel bakış</span><span class="sxs-lookup"><span data-stu-id="1cab4-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
