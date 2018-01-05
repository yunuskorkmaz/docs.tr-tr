---
title: Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cb0cdc9e98dcaf3c9f9879359eff0b31c8435773
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="f4c60-102">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4c60-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="f4c60-103">Kullandığınızda, bir <xref:System.AsyncCallback> zaman uyumsuz işlemi ayrı bir iş parçacığı sonuçlarını işlemek için temsilci seçme, bir durum nesnesi geri aramalar arasında bilgi aktarmak ve son sonucu almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4c60-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="f4c60-104">Bu konuda, uygulama örnekte genişleterek gösterilir [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="f4c60-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4c60-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4c60-105">Example</span></span>  
 <span data-ttu-id="f4c60-106">Aşağıdaki kod örneğinde zaman uyumsuz yöntemleri kullanma gösterilmektedir <xref:System.Net.Dns> kullanıcı tarafından belirtilen bilgisayarların etki alanı adı sistemi (DNS) bilgilerini almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f4c60-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="f4c60-107">Bu örnek tanımlar ve kullanır `HostRequest` durum bilgilerini depolamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f4c60-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="f4c60-108">A `HostRequest` nesne kullanıcı tarafından girilen her bir bilgisayar adı için oluşturulan.</span><span class="sxs-lookup"><span data-stu-id="f4c60-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="f4c60-109">Bu nesne için geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4c60-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="f4c60-110">`ProcessDnsInformation` Yöntemi, bir isteği tamamlayan her zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f4c60-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="f4c60-111">`HostRequest` Nesnesi kullanarak alınır <xref:System.IAsyncResult.AsyncState%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f4c60-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="f4c60-112">`ProcessDnsInformation` Yöntemi kullanan `HostRequest` depolamak için nesne <xref:System.Net.IPHostEntry> istek tarafından döndürülen veya <xref:System.Net.Sockets.SocketException> istek tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f4c60-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="f4c60-113">Tüm istekleri tamamlandığı zaman üzerinden uygulama tekrarlanan `HostRequest` nesneleri ve DNS bilgilerini görüntüler veya <xref:System.Net.Sockets.SocketException> hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="f4c60-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f4c60-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4c60-114">See Also</span></span>  
 [<span data-ttu-id="f4c60-115">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="f4c60-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="f4c60-116">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4c60-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="f4c60-117">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4c60-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
