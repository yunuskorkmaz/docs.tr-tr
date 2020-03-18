---
title: Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73094600"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="7251e-102">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="7251e-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="7251e-103">Ayrı bir <xref:System.AsyncCallback> iş parçacığı içinde asynchronous işlemin sonuçlarını işlemek için bir temsilci kullandığınızda, geri aramaları arasında bilgi aktarmak ve nihai bir sonuç almak için bir durum nesnesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7251e-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="7251e-104">Bu konu, bir [Eşzamanlı İşlemi Sona Erdirmek için Bir AsyncCallback Temsilci kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)örnek genişleterek bu uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="7251e-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7251e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7251e-105">Example</span></span>  
 <span data-ttu-id="7251e-106">Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bilgisayarlar <xref:System.Net.Dns> için Alan Adı Sistemi (DNS) bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7251e-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="7251e-107">Bu örnek, durum `HostRequest` bilgilerini depolamak için sınıfı tanımlar ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="7251e-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="7251e-108">Kullanıcı `HostRequest` tarafından girilen her bilgisayar adı için bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7251e-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="7251e-109">Bu nesne <xref:System.Net.Dns.BeginGetHostByName%2A> yönteme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7251e-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="7251e-110">Yöntem, `ProcessDnsInformation` bir istek her tamamlandığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7251e-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="7251e-111">Nesne `HostRequest` <xref:System.IAsyncResult.AsyncState%2A> özelliği kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="7251e-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="7251e-112">Yöntem, `ProcessDnsInformation` `HostRequest` <xref:System.Net.IPHostEntry> iade edilen isteği veya istek tarafından <xref:System.Net.Sockets.SocketException> atılan bir depoyu depolamak için nesneyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7251e-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="7251e-113">Tüm istekler tamamlandığında, uygulama `HostRequest` nesneler üzerinde yinelenir ve DNS <xref:System.Net.Sockets.SocketException> bilgisini veya hata iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7251e-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7251e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7251e-114">See also</span></span>

- [<span data-ttu-id="7251e-115">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="7251e-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="7251e-116">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7251e-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="7251e-117">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="7251e-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
