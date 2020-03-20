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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047642"
---
# <a name="managing-connections"></a><span data-ttu-id="06c00-102">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="06c00-102">Managing Connections</span></span>
<span data-ttu-id="06c00-103">Veri kaynaklarına bağlanmak için HTTP'yi kullanan uygulamalar, <xref:System.Net.ServicePoint> Internet <xref:System.Net.ServicePointManager> bağlantılarını yönetmek ve optimum ölçek ve performans elde etmelerine yardımcı olmak için .NET Framework'ün ve sınıflarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="06c00-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="06c00-104">**ServicePoint** sınıfı, uygulamanın Internet kaynaklarına erişebileceği bir bitiş noktası olan bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="06c00-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="06c00-105">Her **ServicePoint,** performansı artırmak için en iyi duruma getirme bilgilerini bağlantılar arasında paylaşarak bir Internet sunucusuyla bağlantıları optimize etmeye yardımcı olan bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="06c00-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="06c00-106">Her **ServicePoint,** Tek düzen kaynak tanımlayıcısı (URI) tarafından tanımlanır ve URI'nin şema tanımlayıcısı ve ana bilgisayar parçalarına göre sınıflandırılır.</span><span class="sxs-lookup"><span data-stu-id="06c00-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="06c00-107">Örneğin, aynı **ServicePoint** örneği, UrI'lere `http://www.contoso.com/index.htm` `http://www.contoso.com/news.htm?date=today` istekler sağlar ve aynı şema tanımlayıcısına (http)`www.contoso.com`ve ana bilgisayar parçalarına ( ) sahip olduklarından.</span><span class="sxs-lookup"><span data-stu-id="06c00-107">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="06c00-108">Uygulama zaten sunucuya `www.contoso.com`kalıcı bir bağlantı varsa, iki bağlantı oluşturmak için gerek kaçınarak, her iki isteği almak için bu bağlantıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="06c00-108">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="06c00-109">**ServicePointManager,** **ServicePoint** örneklerinin oluşturulmasını ve yok edilmesini yöneten statik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="06c00-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="06c00-110">**ServicePointManager,** uygulama varolan **ServicePoint** örneklerinin koleksiyonunda olmayan bir Internet kaynağı istediğinde bir **ServicePoint** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06c00-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="06c00-111">**ServicePoint** örnekleri, maksimum boşta kalma sürelerini aştıklarında veya varolan **ServicePoint** örneklerinin sayısı uygulama için en fazla **ServicePoint** örneği sayısını aştığında yok edilir.</span><span class="sxs-lookup"><span data-stu-id="06c00-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="06c00-112">**ServicePointManager'daki**özellikleri <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> ve <xref:System.Net.ServicePointManager.MaxServicePoints%2A> özellikleri ayarlayarak hem varsayılan maksimum boşta kalma süresini hem de en fazla **ServicePoint** örneğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06c00-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="06c00-113">İstemci ve sunucu arasındaki bağlantı sayısı, uygulama verime üzerinde önemli bir etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="06c00-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="06c00-114">Varsayılan olarak, <xref:System.Net.HttpWebRequest> sınıfı kullanan bir uygulama belirli bir sunucuya en fazla iki kalıcı bağlantı kullanır, ancak uygulama başına en fazla bağlantı sayısını ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06c00-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06c00-115">HTTP/1.1 belirtimi, bir uygulamadan bağlantı sayısını sunucu başına iki bağlantıyla sınırlar.</span><span class="sxs-lookup"><span data-stu-id="06c00-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="06c00-116">En uygun bağlantı sayısı, uygulamanın çalıştığı gerçek koşullara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="06c00-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="06c00-117">Uygulamaiçin kullanılabilen bağlantı sayısını artırmak uygulama performansını etkilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="06c00-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="06c00-118">Daha fazla bağlantının etkisini belirlemek için, bağlantı sayısını değiştirerek performans testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06c00-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="06c00-119">Aşağıdaki kod örneğinde gösterildiği gibi, uygulama başlatma <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> sırasında **ServicePointManager** sınıfındaki statik özelliği değiştirerek bir uygulamanın kullandığı bağlantı sayısını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06c00-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="06c00-120">**ServicePointManager.DefaultConnectionLimit** özelliğini değiştirmek, önceden başlatılan **ServicePoint** örneklerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="06c00-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="06c00-121">Aşağıdaki kod, sunucunun `http://www.contoso.com` varolan bir `newLimit` **ServicePoint'teki** bağlantı sınırını depolanan değerle değiştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="06c00-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06c00-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06c00-122">See also</span></span>

- [<span data-ttu-id="06c00-123">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="06c00-123">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="06c00-124">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="06c00-124">Using Application Protocols</span></span>](using-application-protocols.md)
