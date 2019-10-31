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
dev_langs:
- csharp
- vb
ms.openlocfilehash: aed3b18c154d4b7a4390b28fb1f14536690f6b3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121323"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="4cdf8-102">Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme</span><span class="sxs-lookup"><span data-stu-id="4cdf8-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="4cdf8-103">Zaman uyumsuz bir işlemin sonuçlarının, işlem tamamlanana kadar durdurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="4cdf8-104">Zaman uyumsuz bir işlemin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="4cdf8-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="4cdf8-105">Zaman uyumsuz işlemler **bitiş**_OperationName_ yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="4cdf8-106">Bu yaklaşım, bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="4cdf8-107">Zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen <xref:System.IAsyncResult> <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="4cdf8-108">Bu yaklaşımı gösteren bir örnek için bkz. [AsyncWaitHandle kullanarak uygulama yürütmeyi engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="4cdf8-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="4cdf8-109">Zaman uyumsuz bir işlem tamamlanana kadar engellemek için **End**_OperationName_ yöntemini kullanan uygulamalar genellikle **BEGIN**_OperationName_ yöntemini çağırır, işlem yapın ve sonra **End**_OperationName_öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdf8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cdf8-110">Example</span></span>  
 <span data-ttu-id="4cdf8-111">Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistem bilgilerini almak üzere <xref:System.Net.Dns> sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="4cdf8-112">Bu yaklaşım kullanıldığında, bu bağımsız değişkenler gerekli olmadığından, <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` ve `stateObject` parametreleri için `null` (Visual Basic`Nothing`) geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4cdf8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cdf8-113">See also</span></span>

- [<span data-ttu-id="4cdf8-114">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="4cdf8-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="4cdf8-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4cdf8-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
