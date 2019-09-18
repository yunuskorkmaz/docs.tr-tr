---
title: Bağlantıları Yönetme
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
ms.openlocfilehash: 11c17c6893800fce8bbff8f49b3a207c161bcdfa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047642"
---
# <a name="managing-connections"></a><span data-ttu-id="baedb-102">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="baedb-102">Managing Connections</span></span>
<span data-ttu-id="baedb-103">Veri kaynaklarına bağlanmak için http kullanan uygulamalar, Internet bağlantılarını yönetmek ve en uygun <xref:System.Net.ServicePoint> ölçek <xref:System.Net.ServicePointManager> ve performansa ulaşmak için .NET Framework ve sınıflarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="baedb-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="baedb-104">**ServicePoint** sınıfı, uygulamanın Internet kaynaklarına erişim için bağlanabildiği bir uç noktaya sahip bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="baedb-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="baedb-105">Her bir **hizmet noktası** , performansı iyileştirmek için bağlantılar arasında iyileştirme bilgilerini paylaşarak bir Internet sunucusuyla bağlantıları iyileştirmeye yardımcı olan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="baedb-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="baedb-106">Her bir **ServicePoint** bir Tekdüzen Kaynak tanımlayıcısı (URI) tarafından tanımlanır ve, URI 'nin şema tanımlayıcısına ve ana bilgisayar parçalara göre kategorize edilir.</span><span class="sxs-lookup"><span data-stu-id="baedb-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="baedb-107">Örneğin, aynı **ServicePoint** örneği URI `http://www.contoso.com/index.htm` 'lere ve `http://www.contoso.com/news.htm?date=today` aynı düzen tanımlayıcısına (http) ve ana bilgisayar parçalara (`www.contoso.com`) sahip olduklarından istek sağlar.</span><span class="sxs-lookup"><span data-stu-id="baedb-107">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="baedb-108">Uygulamanın zaten sunucuya `www.contoso.com`kalıcı bağlantısı varsa, her iki isteği de almak için bu bağlantıyı kullanır ve iki bağlantı oluşturma gereksinimini ortadan önler.</span><span class="sxs-lookup"><span data-stu-id="baedb-108">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="baedb-109">**ServicePointManager** , **ServicePoint** örneklerinin oluşturulmasını ve yok edilmesini yöneten statik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="baedb-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="baedb-110">**ServicePointManager** , uygulama mevcut **ServicePoint** örnekleri koleksiyonunda olmayan bir Internet kaynağı istediğinde bir **ServicePoint** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baedb-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="baedb-111">**ServicePoint** örnekleri, maksimum boşta kalma süresini aştığında veya var olan **ServicePoint** örneklerinin sayısı, uygulama Için en fazla **ServicePoint** örneği sayısını aşarsa yok edilir.</span><span class="sxs-lookup"><span data-stu-id="baedb-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="baedb-112">**ServicePointManager**'daki <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> ve <xref:System.Net.ServicePointManager.MaxServicePoints%2A> özelliklerini ayarlayarak hem varsayılan en fazla boş süreyi hem de en fazla **ServicePoint** örneği sayısını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baedb-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="baedb-113">İstemci ve sunucu arasındaki bağlantı sayısı, uygulama aktarım hızı üzerinde çarpıcı bir etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="baedb-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="baedb-114">Varsayılan olarak, <xref:System.Net.HttpWebRequest> sınıfı kullanan bir uygulama, belirli bir sunucuya en fazla iki kalıcı bağlantı kullanır, ancak en fazla bağlantı sayısını uygulama başına temelinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baedb-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="baedb-115">HTTP/1.1 belirtimi, bir uygulamadaki bağlantı sayısını sunucu başına iki bağlantı ile sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="baedb-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="baedb-116">En iyi bağlantı sayısı, uygulamanın çalıştığı gerçek koşullara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="baedb-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="baedb-117">Uygulamanın kullanabildiği bağlantı sayısını artırmak uygulama performansını etkilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="baedb-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="baedb-118">Daha fazla bağlantının etkisini öğrenmek için, bağlantı sayısını değiştirerek performans testlerini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="baedb-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="baedb-119">Aşağıdaki kod örneğinde gösterildiği gibi, uygulamanın başlatılmasında <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> **ServicePointManager** sınıfında statik özelliğini değiştirerek uygulamanın kullandığı bağlantı sayısını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baedb-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="baedb-120">**ServicePointManager. DefaultConnectionLimit** özelliğinin değiştirilmesi, daha önce başlatılmış olan **ServicePoint** örneklerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="baedb-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="baedb-121">Aşağıdaki kod, sunucu `http://www.contoso.com` için var olan bir **hizmet noktasındaki** bağlantı sınırının ' de `newLimit`depolanan değere değiştirilmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="baedb-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="baedb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baedb-122">See also</span></span>

- [<span data-ttu-id="baedb-123">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="baedb-123">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="baedb-124">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="baedb-124">Using Application Protocols</span></span>](using-application-protocols.md)
