---
title: "System.Net sınıfları için en iyi yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 90722abbdb4568be115c0ac77007d5f18984df6f
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2018
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="3f8a0-102">System.Net sınıfları için en iyi yöntemler</span><span class="sxs-lookup"><span data-stu-id="3f8a0-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="3f8a0-103">Aşağıdaki önerileri bulunan sınıflar kullanmanıza yardımcı <xref:System.Net> en iyi kendi yararınıza:</span><span class="sxs-lookup"><span data-stu-id="3f8a0-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="3f8a0-104">Aktarım Katmanı Güvenliği (TLS) en iyi yöntemler için bkz: [Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar .NET Framework ile](tls.md).</span><span class="sxs-lookup"><span data-stu-id="3f8a0-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

-   <span data-ttu-id="3f8a0-105">Kullanım <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> alt sınıflar için tür atama yerine mümkün.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="3f8a0-106">Kullanan uygulamalar **WebRequest** ve **WebResponse** yeni Internet protokolleri kapsamlı bir kod değişiklikleri olmadan yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="3f8a0-107">Bir sunucu kullanarak çalıştırın ASP.NET uygulamaları yazarken **System.Net** sınıfları, bu genellikle için zaman uyumsuz yöntemleri kullanmak için bir performans açısından iyi <xref:System.Net.WebRequest.GetResponse%2A> ve <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="3f8a0-108">Bir Internet kaynağına açılan bağlantı sayısı, ağ performansı ve verimliliği hakkında önemli bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="3f8a0-109">**System.Net** varsayılan uygulama ana bilgisayar başına başına iki bağlantı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="3f8a0-110">Ayarı <xref:System.Net.ServicePoint.ConnectionLimit%2A> özelliğinde <xref:System.Net.ServicePoint> için uygulamanızı belirli bir ana bilgisayar için bu sayıyı artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="3f8a0-111">Ayar <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> özelliği, tüm ana bilgisayarlar için bu varsayılan artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="3f8a0-112">Yuva düzeyi protokolleri yazılırken kullanmaya çalıştığınızda <xref:System.Net.Sockets.TcpClient> veya <xref:System.Net.Sockets.UdpClient> mümkün olduğunda doğrudan yazmak yerine bir <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="3f8a0-113">Bu iki istemci sınıfları bağlantı ayrıntılarını işlemek gerek kalmadan TCP ve UDP yuva oluşturulmasını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="3f8a0-114">Kimlik bilgileri gerektiren sitelerine erişirken <xref:System.Net.CredentialCache> sahip her isteği sağladığını yerine kimlik bilgilerinin önbellek oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="3f8a0-115">**CredentialCache** sınıfı oluşturma ve URL temel alınarak kimlik bilgileri sunan sorumluluk gereksinimini azaltır, bir istekle sunmak için uygun kimlik bilgilerini bulmak için önbellek arar.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8a0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-116">See Also</span></span>  
 [<span data-ttu-id="3f8a0-117">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="3f8a0-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
