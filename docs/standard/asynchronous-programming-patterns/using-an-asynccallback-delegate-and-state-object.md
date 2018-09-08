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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46b7839a6bd0086a8ec82e416cdf7aed05707390
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213507"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="232f5-102">Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="232f5-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="232f5-103">Kullandığınızda, bir <xref:System.AsyncCallback> zaman uyumsuz işlemin ayrı bir iş parçacığında sonuçları işlemek için temsilci, bir durum nesnesi geri çağırmalar arasında bilgi geçirmek ve Nihai sonuç almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="232f5-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="232f5-104">Bu konuda, örnekte genişleterek o uygulama gösterilir [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="232f5-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="232f5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="232f5-105">Example</span></span>  
 <span data-ttu-id="232f5-106">Aşağıdaki kod örneği, zaman uyumsuz metotlar kullanma gösterilmektedir <xref:System.Net.Dns> kullanıcı tarafından belirtilen bilgisayarların etki alanı adı sistemi (DNS) bilgilerini almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="232f5-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="232f5-107">Bu örnek, tanımlar ve kullandığı `HostRequest` durum bilgilerini depolamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="232f5-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="232f5-108">A `HostRequest` nesne kullanıcı tarafından girilen her bir bilgisayar adı için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="232f5-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="232f5-109">Bu nesne geçirilir <xref:System.Net.Dns.BeginGetHostByName%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="232f5-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="232f5-110">`ProcessDnsInformation` Yöntemi, bir istek tamamlandıktan her zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="232f5-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="232f5-111">`HostRequest` Nesnesi kullanılarak alınır <xref:System.IAsyncResult.AsyncState%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="232f5-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="232f5-112">`ProcessDnsInformation` Yöntemi kullanan `HostRequest` depolamak için nesne <xref:System.Net.IPHostEntry> istek tarafından döndürülen veya <xref:System.Net.Sockets.SocketException> istek tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="232f5-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="232f5-113">Tüm istekleri tamamlandığı zaman, uygulama üzerinden yinelenir `HostRequest` nesneleri ve DNS bilgilerini görüntüler veya <xref:System.Net.Sockets.SocketException> hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="232f5-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="232f5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="232f5-114">See also</span></span>

- [<span data-ttu-id="232f5-115">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="232f5-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="232f5-116">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="232f5-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
- [<span data-ttu-id="232f5-117">Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="232f5-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
