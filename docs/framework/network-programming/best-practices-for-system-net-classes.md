---
title: System.Net sınıfları için en iyi uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: 0ed97626d86b380565453191f7840c1d1a180dfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689084"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="5a953-102">System.Net sınıfları için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="5a953-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="5a953-103">Aşağıdaki öneriler içinde bulunan sınıfları kullanmanıza yardımcı olacak <xref:System.Net> en iyi kendi lehlerine için:</span><span class="sxs-lookup"><span data-stu-id="5a953-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="5a953-104">Aktarım Katmanı Güvenliği (TLS) en iyi yöntemler için bkz: [Aktarım Katmanı Güvenliği (TLS) en iyi yöntemler .NET Framework ile](tls.md).</span><span class="sxs-lookup"><span data-stu-id="5a953-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

-   <span data-ttu-id="5a953-105">Kullanım <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> mümkün olduğunda yerine alt sınıflar için tür atama.</span><span class="sxs-lookup"><span data-stu-id="5a953-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="5a953-106">Kullanan uygulamalar **WebRequest** ve **WebResponse** yeni Internet protokollerinden kapsamlı bir kod değişikliği gerekmeden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a953-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="5a953-107">Kullanarak sunucu üzerinde çalışan ASP.NET uygulamaları yazarken **System.Net** sınıfları, genellikle zaman uyumsuz yöntemler için kullanılacak bir performans açısından iyi <xref:System.Net.WebRequest.GetResponse%2A> ve <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a953-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="5a953-108">Bir Internet kaynağına için açılan bağlantılar sayısı, ağ performansını ve aktarım hızı üzerinde önemli bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a953-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="5a953-109">**System.Net** varsayılan olarak konak başına uygulama başına iki bağlantı kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a953-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="5a953-110">Ayarı <xref:System.Net.ServicePoint.ConnectionLimit%2A> özelliğinde <xref:System.Net.ServicePoint> için uygulamanızı belirli bir ana bilgisayar için bu sayıyı artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a953-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="5a953-111">Ayarı <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> özelliği, tüm konaklar için bu varsayılan artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a953-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="5a953-112">Yuva düzeyi protokolleri yazarken kullanmaya çalıştığınızda <xref:System.Net.Sockets.TcpClient> veya <xref:System.Net.Sockets.UdpClient> mümkün olduğunda doğrudan yazmak yerine bir <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="5a953-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="5a953-113">Bu iki istemci sınıfları bağlantı ayrıntılarını işlemek gerek kalmadan TCP ve UDP yuva oluşturulmasını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="5a953-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="5a953-114">Kimlik bilgileri gerektiren siteleri erişirken <xref:System.Net.CredentialCache> bunları her istekle sağlama yerine kimlik bilgileri önbellek oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5a953-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="5a953-115">**CredentialCache** sınıfı önbellek oluşturma ve sunma URL'sini temel alarak kimlik bilgileri sorumluluğu, yoğun bir istekle sunmak için uygun kimlik bilgilerini bulmak için arama yapar.</span><span class="sxs-lookup"><span data-stu-id="5a953-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a953-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a953-116">See also</span></span>
- [<span data-ttu-id="5a953-117">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="5a953-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
