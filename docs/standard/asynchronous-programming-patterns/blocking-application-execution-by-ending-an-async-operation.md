---
title: "Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.openlocfilehash: ccca6e1e4f6b5cdf098018b59426fb2262e2b346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="1c71a-102">Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme</span><span class="sxs-lookup"><span data-stu-id="1c71a-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="1c71a-103">İşlemi tamamlanana kadar diğer iş zaman uyumsuz bir işlem sonuçları için beklenirken yapmak için devam edemiyor uygulamaları engellemelidir.</span><span class="sxs-lookup"><span data-stu-id="1c71a-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="1c71a-104">Bir zaman uyumsuz bir işlemin tamamlanması beklenirken, uygulamanın ana iş parçacığı engellemek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="1c71a-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="1c71a-105">Zaman uyumsuz işlemleri çağrısı **son** *OperationName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c71a-105">Call the asynchronous operations **End** *OperationName* method.</span></span> <span data-ttu-id="1c71a-106">Bu yaklaşım, bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c71a-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="1c71a-107">Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak** *OperationName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c71a-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="1c71a-108">Bu yaklaşım gösteren bir örnek için bkz: [engelleme uygulama yürütme kullanarak bir AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="1c71a-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="1c71a-109">Kullanan uygulamalar **son** *OperationName* yöntemi zaman uyumsuz bir işlem tamamlanana kadar engellemek için genellikle çağıracaktır **başlamak**  *OperationName* yöntemi, işlemin sonuçlarını yapılabilir, ardından çağıran herhangi bir iş gerçekleştirmek **son** *OperationName*.</span><span class="sxs-lookup"><span data-stu-id="1c71a-109">Applications that use the **End** *OperationName* method to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then call **End** *OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c71a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c71a-110">Example</span></span>  
 <span data-ttu-id="1c71a-111">Aşağıdaki kod örneğinde zaman uyumsuz yöntemleri kullanma gösterilmektedir <xref:System.Net.Dns> sınıfı bir kullanıcı tarafından belirtilen bilgisayar için etki alanı adı sistemi bilgileri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="1c71a-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="1c71a-112">Unutmayın `null` (`Nothing` Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` ve `stateObject` parametreleri bu bağımsız değişkenler bu yaklaşımı kullanarak, gerekli olmadığından.</span><span class="sxs-lookup"><span data-stu-id="1c71a-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1c71a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c71a-113">See Also</span></span>  
 [<span data-ttu-id="1c71a-114">Olay tabanlı zaman uyumsuz desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="1c71a-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="1c71a-115">Olay tabanlı zaman uyumsuz desene genel bakış</span><span class="sxs-lookup"><span data-stu-id="1c71a-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
