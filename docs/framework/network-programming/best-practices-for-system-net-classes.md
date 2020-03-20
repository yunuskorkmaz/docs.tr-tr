---
title: System.Net Sınıfları için En İyi Yöntemler
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
ms.openlocfilehash: c7324dcbc27c95c7d799592700d46c195e7d952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048888"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="848b0-102">System.Net Sınıfları için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="848b0-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="848b0-103">Aşağıdaki öneriler, içinde bulunan sınıfları <xref:System.Net> en iyi şekilde kullanmanıza yardımcı olacaktır:</span><span class="sxs-lookup"><span data-stu-id="848b0-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="848b0-104">Aktarım Katmanı Güvenliği (TLS) için en iyi uygulamalar için [,.NET Framework ile Taşıma Katmanı Güvenliği (TLS) en iyi uygulamalarına](tls.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="848b0-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="848b0-105">Soyundan <xref:System.Net.WebResponse> gelen sınıflara yazı dökümü yerine mümkün olduğunca kullanın. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="848b0-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="848b0-106">**WebRequest** ve **WebResponse** kullanan uygulamalar, kapsamlı kod değişikliklerine gerek kalmadan yeni Internet protokollerinden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="848b0-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="848b0-107">**System.Net** sınıflarını kullanarak bir sunucuda çalışan ASP.NET uygulamaları yazarken, performans açısından, asynchronous yöntemlerini <xref:System.Net.WebRequest.GetResponse%2A> kullanmak <xref:System.Net.WebResponse.GetResponseStream%2A>genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="848b0-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="848b0-108">Bir Internet kaynağına açılan bağlantı sayısının ağ performansı ve iş bölümü üzerinde önemli bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="848b0-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="848b0-109">**System.Net** varsayılan olarak ana bilgisayar başına uygulama başına iki bağlantı kullanır.</span><span class="sxs-lookup"><span data-stu-id="848b0-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="848b0-110">Uygulamanız <xref:System.Net.ServicePoint.ConnectionLimit%2A> <xref:System.Net.ServicePoint> için özelliği ayarlamak, belirli bir ana bilgisayar için bu sayıyı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="848b0-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="848b0-111">Özelliği <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> ayarlamak, tüm ana bilgisayarlar için bu varsayılanı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="848b0-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="848b0-112">Soket düzeyinde protokoller yazarken, <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.UdpClient> doğrudan bir <xref:System.Net.Sockets.Socket>' ye yazmak yerine veya mümkün olduğunda kullanmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="848b0-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="848b0-113">Bu iki istemci sınıfı, bağlantının ayrıntılarını işlemenizi gerektirmeden TCP ve UDP soketlerinin oluşturulmasını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="848b0-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="848b0-114">Kimlik bilgileri gerektiren sitelere erişirken, her isteği sağlamak yerine bir kimlik önbelleği oluşturmak için <xref:System.Net.CredentialCache> sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="848b0-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="848b0-115">**Kimlik BilgisiÖnbellek** sınıfı, bir isteksunmak için uygun kimlik bilgilerini bulmak için önbelleği arar ve URL'ye dayalı kimlik bilgileri oluşturma ve sunma sorumluluğunuzdan sizi rahatlatır.</span><span class="sxs-lookup"><span data-stu-id="848b0-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848b0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="848b0-116">See also</span></span>

- [<span data-ttu-id="848b0-117">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="848b0-117">Network Programming in the .NET Framework</span></span>](index.md)
