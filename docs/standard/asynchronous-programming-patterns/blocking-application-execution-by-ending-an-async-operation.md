---
title: Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: 63ecff45e39f3d3813d3f817a2cc55c6c35f5b3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870181"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="46c24-102">Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme</span><span class="sxs-lookup"><span data-stu-id="46c24-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="46c24-103">İşlem tamamlanana kadar zaman uyumsuz bir işlemin sonuçları için beklerken, diğer iş yapmak için devam edemiyor uygulamaları engellemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46c24-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="46c24-104">Uygulamanızın ana iş parçacığı bir zaman uyumsuz bir işlemin tamamlanması beklenirken engellemek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="46c24-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="46c24-105">Zaman uyumsuz işlemleri çağırmak **son**_OperationName_ yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46c24-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="46c24-106">Bu yaklaşım, bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46c24-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="46c24-107">Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak**_OperationName_ yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46c24-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="46c24-108">Bu yaklaşım gösteren bir örnek için bkz: [engelleme uygulama yürütme kullanarak bir AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="46c24-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="46c24-109">Kullanan uygulamalar **son**_OperationName_ bir zaman uyumsuz işlem tamamlanana kadar engelleyin yöntemi genellikle çağıracaktır **başlamak**  _OperationName_ yöntemi, işlemin sonuçlarını gerek kalmadan yapılabilir ve sonra bir iş gerçekleştirmek **son**_OperationName_.</span><span class="sxs-lookup"><span data-stu-id="46c24-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c24-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="46c24-110">Example</span></span>  
 <span data-ttu-id="46c24-111">Aşağıdaki kod örneği, zaman uyumsuz metotlar kullanma gösterilmektedir <xref:System.Net.Dns> sınıfı, kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistemi bilgileri alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="46c24-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="46c24-112">Unutmayın `null` (`Nothing` Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` ve `stateObject` parametreleri bu bağımsız değişkenler bu yaklaşım kullanırken gerekli olmadığından.</span><span class="sxs-lookup"><span data-stu-id="46c24-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="46c24-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c24-113">See also</span></span>

- [<span data-ttu-id="46c24-114">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="46c24-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="46c24-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="46c24-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
