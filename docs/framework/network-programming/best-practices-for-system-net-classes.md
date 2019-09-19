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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048888"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="e2c4e-102">System.Net Sınıfları için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e2c4e-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="e2c4e-103">Aşağıdaki öneriler, ' de <xref:System.Net> bulunan sınıfları en iyi avantajları ile kullanmanıza yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="e2c4e-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="e2c4e-104">Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları için bkz. [.NET Framework Ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](tls.md).</span><span class="sxs-lookup"><span data-stu-id="e2c4e-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="e2c4e-105">Alt <xref:System.Net.WebRequest> sınıflara <xref:System.Net.WebResponse> tür atama yapmak yerine ve mümkün olan her seferinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="e2c4e-106">**WebRequest** ve **WebResponse** kullanan uygulamalar, kapsamlı kod değişikliklerine gerek duymadan yeni Internet protokollerinden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="e2c4e-107">**System.net** sınıflarını kullanarak bir sunucuda çalışan ASP.NET uygulamaları yazarken, bir performans açısından, ve <xref:System.Net.WebRequest.GetResponse%2A> <xref:System.Net.WebResponse.GetResponseStream%2A>için zaman uyumsuz yöntemleri kullanmak genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="e2c4e-108">Bir Internet kaynağına açılan bağlantı sayısı, ağ performansı ve verimlilik üzerinde önemli bir etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="e2c4e-109">**System.net** , varsayılan olarak her konak için uygulama başına iki bağlantı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="e2c4e-110">Uygulamanız için içindeki <xref:System.Net.ServicePoint> özelliğinin ayarlanması, belirli bir konak için bu sayıyı artırabilir. <xref:System.Net.ServicePoint.ConnectionLimit%2A></span><span class="sxs-lookup"><span data-stu-id="e2c4e-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="e2c4e-111">Özelliği ayarlamak <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> , tüm konaklar için bu varsayılanı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="e2c4e-112">Yuva düzeyi protokoller yazarken, ' a <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.Socket>doğrudan yazmak yerine veya <xref:System.Net.Sockets.UdpClient> mümkün olduğunca kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="e2c4e-113">Bu iki istemci sınıfı, bağlantının ayrıntılarını işleyebilmeniz gerekmeden TCP ve UDP yuvaları oluşturmayı kapsüller.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="e2c4e-114">Kimlik bilgileri gerektiren sitelere erişirken, her istekte bunları <xref:System.Net.CredentialCache> sağlamak yerine, kimlik bilgilerinin bir önbelleğini oluşturmak için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="e2c4e-115">**CredentialCache** sınıfı, bir istekle birlikte sunmak üzere uygun kimlik bilgisini bulmak için önbelleği arar, bu da URL 'ye göre kimlik bilgileri oluşturma ve sunma sorumluluğunu ortadan kaldırmak.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c4e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2c4e-116">See also</span></span>

- [<span data-ttu-id="e2c4e-117">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="e2c4e-117">Network Programming in the .NET Framework</span></span>](index.md)
