---
description: 'Hakkında daha fazla bilgi edinin: bir AsyncCallback temsilcisi ve durum nesnesi kullanma'
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
ms.openlocfilehash: b7ffb3180d7e2e15a12d3bf0f98311b0310112e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732242"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="5ff2d-103">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ff2d-103">Using an AsyncCallback Delegate and State Object</span></span>

<span data-ttu-id="5ff2d-104"><xref:System.AsyncCallback>Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir temsilci kullandığınızda, geri çağrılar arasında bilgi geçirmek ve nihai sonucu almak için bir durum nesnesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-104">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="5ff2d-105">Bu konuda, [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)içindeki örneği genişleterek bu alıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-105">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff2d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ff2d-106">Example</span></span>  

 <span data-ttu-id="5ff2d-107">Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bilgisayarlar Için etki alanı adı sistemi (DNS) bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-107">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="5ff2d-108">Bu örnek, `HostRequest` durum bilgilerini depolamak için sınıfını tanımlar ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-108">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="5ff2d-109">`HostRequest`Kullanıcı tarafından girilen her bilgisayar adı için bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-109">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="5ff2d-110">Bu nesne <xref:System.Net.Dns.BeginGetHostByName%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-110">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="5ff2d-111">`ProcessDnsInformation`Yöntemi, istek her tamamlandığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-111">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="5ff2d-112">`HostRequest`Nesnesi, özelliği kullanılarak alınır <xref:System.IAsyncResult.AsyncState%2A> .</span><span class="sxs-lookup"><span data-stu-id="5ff2d-112">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="5ff2d-113">`ProcessDnsInformation`Yöntemi, `HostRequest` <xref:System.Net.IPHostEntry> istek tarafından döndürülen veya istek tarafından oluşturulan bir öğesini depolamak için nesnesini kullanır <xref:System.Net.Sockets.SocketException> .</span><span class="sxs-lookup"><span data-stu-id="5ff2d-113">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="5ff2d-114">Tüm istekler tamamlandığında, uygulama nesneler üzerinde dolaşır `HostRequest` ve DNS bilgilerini veya <xref:System.Net.Sockets.SocketException> hata iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-114">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5ff2d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ff2d-115">See also</span></span>

- [<span data-ttu-id="5ff2d-116">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="5ff2d-116">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="5ff2d-117">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ff2d-117">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="5ff2d-118">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ff2d-118">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
