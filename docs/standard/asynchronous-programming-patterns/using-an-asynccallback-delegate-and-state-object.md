---
title: Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: 0a33c852d822e7d25d14ab17324459ec005853f9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829149"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="ef361-102">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef361-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="ef361-103"><xref:System.AsyncCallback>Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir temsilci kullandığınızda, geri çağrılar arasında bilgi geçirmek ve nihai sonucu almak için bir durum nesnesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef361-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="ef361-104">Bu konuda, [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)içindeki örneği genişleterek bu alıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef361-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef361-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef361-105">Example</span></span>  
 <span data-ttu-id="ef361-106">Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bilgisayarlar Için etki alanı adı sistemi (DNS) bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef361-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="ef361-107">Bu örnek, `HostRequest` durum bilgilerini depolamak için sınıfını tanımlar ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef361-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="ef361-108">`HostRequest`Kullanıcı tarafından girilen her bilgisayar adı için bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef361-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="ef361-109">Bu nesne <xref:System.Net.Dns.BeginGetHostByName%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ef361-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="ef361-110">`ProcessDnsInformation`Yöntemi, istek her tamamlandığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ef361-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="ef361-111">`HostRequest`Nesnesi, özelliği kullanılarak alınır <xref:System.IAsyncResult.AsyncState%2A> .</span><span class="sxs-lookup"><span data-stu-id="ef361-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="ef361-112">`ProcessDnsInformation`Yöntemi, `HostRequest` <xref:System.Net.IPHostEntry> istek tarafından döndürülen veya istek tarafından oluşturulan bir öğesini depolamak için nesnesini kullanır <xref:System.Net.Sockets.SocketException> .</span><span class="sxs-lookup"><span data-stu-id="ef361-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="ef361-113">Tüm istekler tamamlandığında, uygulama nesneler üzerinde dolaşır `HostRequest` ve DNS bilgilerini veya <xref:System.Net.Sockets.SocketException> hata iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ef361-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ef361-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef361-114">See also</span></span>

- [<span data-ttu-id="ef361-115">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="ef361-115">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="ef361-116">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ef361-116">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="ef361-117">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef361-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
