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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121323"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="b371a-102">Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme</span><span class="sxs-lookup"><span data-stu-id="b371a-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="b371a-103">Eşzamanlı işlemin sonuçlarını beklerken başka işler yapmaya devam edemeyen uygulamaların işlem tamamlanana kadar engellenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b371a-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="b371a-104">Asynchronous işleminin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b371a-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="b371a-105">Eşzamanlı işlemleri **Son**_İşlemName_ yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="b371a-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="b371a-106">Bu yaklaşım bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b371a-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="b371a-107">Eşzamanlı işlemin **Begin**_OperationName_ yöntemiyle döndürülen <xref:System.IAsyncResult> özelliği kullanın. <xref:System.IAsyncResult.AsyncWaitHandle%2A></span><span class="sxs-lookup"><span data-stu-id="b371a-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="b371a-108">Bu yaklaşımı gösteren bir örnek için, [bkz.](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)</span><span class="sxs-lookup"><span data-stu-id="b371a-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="b371a-109">Bir eşzamanlı işlem tamamlanana kadar engellemeyi engellemek için **Son**_İşlem Adı_ yöntemini kullanan uygulamalar genellikle_İşlemNameyi_ **Başlat**yöntemini çağırır, işlemin sonuçları olmadan yapılabilecek herhangi bir işi gerçekleştirir ve ardından **Son**_İşlem Name'yi_çağırır.</span><span class="sxs-lookup"><span data-stu-id="b371a-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b371a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b371a-110">Example</span></span>  
 <span data-ttu-id="b371a-111">Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bir <xref:System.Net.Dns> bilgisayar için Alan Adı Sistemi bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b371a-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="b371a-112">`null` Bu yaklaşım`Nothing` kullanılırken bu bağımsız <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` değişkenler gerekli olmadığından ( Visual Basic'te) `stateObject` parametreler için geçirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b371a-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b371a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b371a-113">See also</span></span>

- [<span data-ttu-id="b371a-114">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="b371a-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="b371a-115">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b371a-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
