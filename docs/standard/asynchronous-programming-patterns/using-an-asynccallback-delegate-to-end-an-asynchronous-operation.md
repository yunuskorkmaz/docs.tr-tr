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
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130931"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="a9e15-102">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9e15-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="a9e15-103">Eşzamanlı işlemin sonuçlarını beklerken başka bir iş yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellememelidir.</span><span class="sxs-lookup"><span data-stu-id="a9e15-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="a9e15-104">Eşzamanlı işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için aşağıdaki seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a9e15-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="a9e15-105">Ayrı <xref:System.AsyncCallback> bir iş parçacığı içinde asynchronous işlemin sonuçlarını işlemek için bir temsilci kullanın.</span><span class="sxs-lookup"><span data-stu-id="a9e15-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="a9e15-106">Bu yaklaşım bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a9e15-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="a9e15-107">İşlemin <xref:System.IAsyncResult.IsCompleted%2A> tamamlanıp <xref:System.IAsyncResult> tamamlanmadığını belirlemek için eşzamanlı işlemin **Begin**_OperationName_ yöntemi yle döndürülen özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="a9e15-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="a9e15-108">Bu yaklaşımı gösteren bir örnek için, bir [Eşzamanlı İşlemin Durumu Için Yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a9e15-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9e15-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9e15-109">Example</span></span>  
 <span data-ttu-id="a9e15-110">Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bilgisayarlar <xref:System.Net.Dns> için Alan Adı Sistemi (DNS) bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9e15-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="a9e15-111">Bu örnek, <xref:System.AsyncCallback> `ProcessDnsInformation` yönteme başvuran bir temsilci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9e15-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="a9e15-112">Bu yöntem, DNS bilgileri için her bir eşzamanlı istek için bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a9e15-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="a9e15-113">Kullanıcı tarafından belirtilen ana bilgisayar parametreye <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> geçirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a9e15-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="a9e15-114">Daha karmaşık bir durum nesnesi tanımlamayı ve kullanmayı gösteren [bir](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)örnek için bkz.</span><span class="sxs-lookup"><span data-stu-id="a9e15-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a9e15-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9e15-115">See also</span></span>

- [<span data-ttu-id="a9e15-116">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="a9e15-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="a9e15-117">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a9e15-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="a9e15-118">IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma </span><span class="sxs-lookup"><span data-stu-id="a9e15-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="a9e15-119">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9e15-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
