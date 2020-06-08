---
title: Bağlantıları Yönetme
description: Veri kaynakları için HTTP kullanan uygulamaların bağlantıları yönetmek için .NET Framework ServicePoint ve ServicePointManager sınıflarını nasıl kullanabileceği hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 124dff1b104e323b929d13f73cf17d740e747c32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502294"
---
# <a name="managing-connections"></a><span data-ttu-id="fc11b-103">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="fc11b-103">Managing Connections</span></span>
<span data-ttu-id="fc11b-104">Veri kaynaklarına bağlanmak için HTTP kullanan uygulamalar, <xref:System.Net.ServicePoint> <xref:System.Net.ServicePointManager> Internet bağlantılarını yönetmek ve en uygun ölçek ve performansa ulaşmak için .NET Framework ve sınıflarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="fc11b-104">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="fc11b-105">**ServicePoint** sınıfı, uygulamanın Internet kaynaklarına erişim için bağlanabildiği bir uç noktaya sahip bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc11b-105">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="fc11b-106">Her bir **hizmet noktası** , performansı iyileştirmek için bağlantılar arasında iyileştirme bilgilerini paylaşarak bir Internet sunucusuyla bağlantıları iyileştirmeye yardımcı olan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fc11b-106">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="fc11b-107">Her bir **ServicePoint** bir Tekdüzen Kaynak tanımlayıcısı (URI) tarafından tanımlanır ve, URI 'nin şema tanımlayıcısına ve ana bilgisayar parçalara göre kategorize edilir.</span><span class="sxs-lookup"><span data-stu-id="fc11b-107">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="fc11b-108">Örneğin, aynı **ServicePoint** örneği URI 'lere `http://www.contoso.com/index.htm` ve `http://www.contoso.com/news.htm?date=today` aynı düzen tanımlayıcısına (http) ve ana bilgisayar parçalara () sahip olduklarından istek sağlar `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="fc11b-108">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="fc11b-109">Uygulamanın zaten sunucuya kalıcı bağlantısı varsa `www.contoso.com` , her iki isteği de almak için bu bağlantıyı kullanır ve iki bağlantı oluşturma gereksinimini ortadan önler.</span><span class="sxs-lookup"><span data-stu-id="fc11b-109">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="fc11b-110">**ServicePointManager** , **ServicePoint** örneklerinin oluşturulmasını ve yok edilmesini yöneten statik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="fc11b-110">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="fc11b-111">**ServicePointManager** , uygulama mevcut **ServicePoint** örnekleri koleksiyonunda olmayan bir Internet kaynağı istediğinde bir **ServicePoint** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc11b-111">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="fc11b-112">**ServicePoint** örnekleri, maksimum boşta kalma süresini aştığında veya var olan **ServicePoint** örneklerinin sayısı, uygulama Için en fazla **ServicePoint** örneği sayısını aşarsa yok edilir.</span><span class="sxs-lookup"><span data-stu-id="fc11b-112">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="fc11b-113">**ServicePoint** <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> <xref:System.Net.ServicePointManager.MaxServicePoints%2A> **ServicePointManager**'daki ve özelliklerini ayarlayarak hem varsayılan en fazla boş süreyi hem de en fazla ServicePoint örneği sayısını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc11b-113">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="fc11b-114">İstemci ve sunucu arasındaki bağlantı sayısı, uygulama aktarım hızı üzerinde çarpıcı bir etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc11b-114">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="fc11b-115">Varsayılan olarak, sınıfı kullanan bir uygulama, <xref:System.Net.HttpWebRequest> belirli bir sunucuya en fazla iki kalıcı bağlantı kullanır, ancak en fazla bağlantı sayısını uygulama başına temelinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc11b-115">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc11b-116">HTTP/1.1 belirtimi, bir uygulamadaki bağlantı sayısını sunucu başına iki bağlantı ile sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="fc11b-116">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="fc11b-117">En iyi bağlantı sayısı, uygulamanın çalıştığı gerçek koşullara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fc11b-117">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="fc11b-118">Uygulamanın kullanabildiği bağlantı sayısını artırmak uygulama performansını etkilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="fc11b-118">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="fc11b-119">Daha fazla bağlantının etkisini öğrenmek için, bağlantı sayısını değiştirerek performans testlerini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fc11b-119">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="fc11b-120"><xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A>Aşağıdaki kod örneğinde gösterildiği gibi, uygulamanın başlatılmasında **ServicePointManager** sınıfında statik özelliğini değiştirerek uygulamanın kullandığı bağlantı sayısını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc11b-120">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="fc11b-121">**ServicePointManager. DefaultConnectionLimit** özelliğinin değiştirilmesi, daha önce başlatılmış olan **ServicePoint** örneklerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="fc11b-121">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="fc11b-122">Aşağıdaki kod, sunucu için var olan bir **hizmet noktasındaki** bağlantı sınırının `http://www.contoso.com` ' de depolanan değere değiştirilmesini gösterir `newLimit` .</span><span class="sxs-lookup"><span data-stu-id="fc11b-122">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc11b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc11b-123">See also</span></span>

- [<span data-ttu-id="fc11b-124">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="fc11b-124">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="fc11b-125">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc11b-125">Using Application Protocols</span></span>](using-application-protocols.md)
