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
ms.openlocfilehash: 16b5a297c13cd9096548ed489e4994b72a48da67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121433"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="17b49-102">Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme</span><span class="sxs-lookup"><span data-stu-id="17b49-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="17b49-103">Eşzamanlı işlemin sonuçlarını beklerken başka işler yapmaya devam edemeyen uygulamaların işlem tamamlanana kadar engellenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="17b49-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="17b49-104">Asynchronous işleminin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="17b49-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="17b49-105">Eşzamanlı işlemin **Begin**_OperationName_ yöntemiyle döndürülen <xref:System.IAsyncResult> özelliği kullanın. <xref:System.IAsyncResult.AsyncWaitHandle%2A></span><span class="sxs-lookup"><span data-stu-id="17b49-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="17b49-106">Bu yaklaşım bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="17b49-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="17b49-107">Eşzamanlı işlemin **Son**_İşlemName_ yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="17b49-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="17b49-108">Bu yaklaşımı gösteren [bir](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)örnek için bkz.</span><span class="sxs-lookup"><span data-stu-id="17b49-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="17b49-109">Bir eşzamanlı işlem tamamlanana kadar engellemek için bir veya daha fazla <xref:System.Threading.WaitHandle> nesne kullanan uygulamalar genellikle **Begin**_OperationName_ yöntemini çağırır, işlem sonuçları olmadan yapılabilecek herhangi bir işi gerçekleştirir ve eşsenkronize işlem(ler) tamamlanana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="17b49-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="17b49-110">Bir uygulama kullanarak <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemlerden birini arayarak tek <xref:System.IAsyncResult.AsyncWaitHandle%2A>bir işlem üzerinde engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="17b49-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="17b49-111">Bir eşyokuz işlemleri kümesinin tamamlanmasını beklerken engellemek <xref:System.IAsyncResult.AsyncWaitHandle%2A> için, ilişkili nesneleri bir dizide depolayın ve yöntemlerden birini çağırın. <xref:System.Threading.WaitHandle.WaitAll%2A></span><span class="sxs-lookup"><span data-stu-id="17b49-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="17b49-112">Eşiş işlemleri kümesinin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesneleri bir dizide depolayın ve <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemlerden birini arayın.</span><span class="sxs-lookup"><span data-stu-id="17b49-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17b49-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="17b49-113">Example</span></span>  
 <span data-ttu-id="17b49-114">Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bir bilgisayar için Alan Adı Sistemi bilgilerini almak için DNS sınıfında eşzamanlı yöntemler ini gösterir.</span><span class="sxs-lookup"><span data-stu-id="17b49-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="17b49-115">Örnek, eşzamanlı işlemle <xref:System.Threading.WaitHandle> ilişkili kullanımıengellemeyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="17b49-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="17b49-116">`null` Bu yaklaşımı`Nothing` kullanırken gerekli olmadığı <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` için `stateObject` (Visual Basic'te) parametreler için geçirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="17b49-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="17b49-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17b49-117">See also</span></span>

- [<span data-ttu-id="17b49-118">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="17b49-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="17b49-119">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="17b49-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
