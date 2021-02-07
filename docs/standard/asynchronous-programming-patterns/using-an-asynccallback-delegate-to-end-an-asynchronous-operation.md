---
description: 'Daha fazla bilgi edinin: zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma'
title: Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c97be1b9dbf225cfb76f8d9392269297fc1d123c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732195"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="0ed39-103">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="0ed39-103">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>

<span data-ttu-id="0ed39-104">Zaman uyumsuz bir işlemin sonuçlarını beklerken diğer işleri yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellemez.</span><span class="sxs-lookup"><span data-stu-id="0ed39-104">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="0ed39-105">Zaman uyumsuz bir işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için şu seçeneklerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ed39-105">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="0ed39-106"><xref:System.AsyncCallback>Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir temsilci kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ed39-106">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="0ed39-107">Bu yaklaşım, bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ed39-107">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="0ed39-108"><xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> İşlemin tamamlanıp tamamlanmadığını anlamak için, zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ed39-108">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="0ed39-109">Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemin durumu Için yoklama](polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="0ed39-109">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ed39-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ed39-110">Example</span></span>  

 <span data-ttu-id="0ed39-111">Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bilgisayarlar Için etki alanı adı sistemi (DNS) bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ed39-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="0ed39-112">Bu örnek <xref:System.AsyncCallback> , yöntemine başvuran bir temsilci oluşturur `ProcessDnsInformation` .</span><span class="sxs-lookup"><span data-stu-id="0ed39-112">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="0ed39-113">Bu yöntem, DNS bilgileri için her zaman uyumsuz istek için bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0ed39-113">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="0ed39-114">Kullanıcı tarafından belirtilen konağın parametreye geçtiğini unutmayın <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0ed39-114">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="0ed39-115">Daha karmaşık bir durum nesnesini tanımlamayı ve kullanmayı gösteren bir örnek için bkz. [AsyncCallback temsilcisi ve durum nesnesi kullanma](using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="0ed39-115">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0ed39-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ed39-116">See also</span></span>

- [<span data-ttu-id="0ed39-117">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="0ed39-117">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="0ed39-118">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ed39-118">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="0ed39-119">IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="0ed39-119">Calling Asynchronous Methods Using IAsyncResult</span></span>](calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="0ed39-120">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="0ed39-120">Using an AsyncCallback Delegate and State Object</span></span>](using-an-asynccallback-delegate-and-state-object.md)
