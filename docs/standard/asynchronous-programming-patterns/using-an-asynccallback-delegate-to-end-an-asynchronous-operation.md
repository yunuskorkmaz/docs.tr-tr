---
title: Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 856273c9592aa32feb3e8cc66c850cb34ad0812f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079142"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="8ced0-102">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ced0-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="8ced0-103">Zaman uyumsuz bir işlemin sonuçları için beklenirken diğer işlerinizi yapabilirsiniz uygulamalar işlem tamamlanana kadar bekleyen Engellemesi gereken değil.</span><span class="sxs-lookup"><span data-stu-id="8ced0-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="8ced0-104">Bir zaman uyumsuz bir işlemin tamamlanması beklenirken yönergeleri yürütme devam etmek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="8ced0-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="8ced0-105">Kullanım bir <xref:System.AsyncCallback> zaman uyumsuz işlemin ayrı bir iş parçacığında sonuçları işlemek için temsilci.</span><span class="sxs-lookup"><span data-stu-id="8ced0-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="8ced0-106">Bu yaklaşım, bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ced0-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="8ced0-107">Kullanım <xref:System.IAsyncResult.IsCompleted%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen \**başlamak \*\*\* OperationName* işleminin tamamlanıp tamamlanmadığını belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ced0-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's \**Begin\*\*\*OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="8ced0-108">Bu yaklaşım gösteren bir örnek için bkz: [zaman uyumsuz bir işlemin durumu için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="8ced0-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ced0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ced0-109">Example</span></span>  
 <span data-ttu-id="8ced0-110">Aşağıdaki kod örneği, zaman uyumsuz metotlar kullanma gösterilmektedir <xref:System.Net.Dns> kullanıcı tarafından belirtilen bilgisayarların etki alanı adı sistemi (DNS) bilgilerini almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="8ced0-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="8ced0-111">Bu örnekte bir <xref:System.AsyncCallback> başvuran temsilci `ProcessDnsInformation` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ced0-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="8ced0-112">Bu yöntem, DNS bilgileri için her zaman uyumsuz istek için bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8ced0-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="8ced0-113">Kullanıcı tarafından belirtilen konak geçirilir Not <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametresi.</span><span class="sxs-lookup"><span data-stu-id="8ced0-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="8ced0-114">Tanımlama ve daha karmaşık bir durum nesnesi kullanma gösteren bir örnek için bkz: [bir AsyncCallback temsilcisi ve durum nesnesi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="8ced0-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8ced0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ced0-115">See also</span></span>

- [<span data-ttu-id="8ced0-116">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="8ced0-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="8ced0-117">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8ced0-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
- [<span data-ttu-id="8ced0-118">IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="8ced0-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
- [<span data-ttu-id="8ced0-119">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ced0-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
