---
title: System.Net Sınıfları için En İyi Yöntemler
description: System.Net ' de bulunan sınıfları .NET Framework programlamada en iyi şekilde kullanmak için bu önerileri izleyin.
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
ms.openlocfilehash: 583fa5e57c7c4d60252dddfd425596e7acad7c0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502684"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="02bb8-103">System.Net Sınıfları için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="02bb8-103">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="02bb8-104">Aşağıdaki öneriler, ' de bulunan sınıfları <xref:System.Net> en iyi avantajları ile kullanmanıza yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="02bb8-104">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="02bb8-105">Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları için bkz. [.NET Framework Ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](tls.md).</span><span class="sxs-lookup"><span data-stu-id="02bb8-105">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="02bb8-106">Alt <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> sınıflara tür atama yapmak yerine ve mümkün olan her seferinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="02bb8-106">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="02bb8-107">**WebRequest** ve **WebResponse** kullanan uygulamalar, kapsamlı kod değişikliklerine gerek duymadan yeni Internet protokollerinden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="02bb8-107">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="02bb8-108">**System.net** sınıflarını kullanarak bir sunucuda çalışan ASP.NET uygulamaları yazarken, bir performans açısından, ve için zaman uyumsuz yöntemleri kullanmak genellikle daha iyidir <xref:System.Net.WebRequest.GetResponse%2A> <xref:System.Net.WebResponse.GetResponseStream%2A> .</span><span class="sxs-lookup"><span data-stu-id="02bb8-108">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="02bb8-109">Bir Internet kaynağına açılan bağlantı sayısı, ağ performansı ve verimlilik üzerinde önemli bir etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="02bb8-109">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="02bb8-110">**System.net** , varsayılan olarak her konak için uygulama başına iki bağlantı kullanır.</span><span class="sxs-lookup"><span data-stu-id="02bb8-110">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="02bb8-111"><xref:System.Net.ServicePoint.ConnectionLimit%2A>Uygulamanız için içindeki özelliğinin ayarlanması, <xref:System.Net.ServicePoint> belirli bir konak için bu sayıyı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="02bb8-111">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="02bb8-112">Özelliği ayarlamak, <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> tüm konaklar için bu varsayılanı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="02bb8-112">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="02bb8-113">Yuva düzeyi protokoller yazarken, ' <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.UdpClient> a doğrudan yazmak yerine veya mümkün olduğunca kullanmayı deneyin <xref:System.Net.Sockets.Socket> .</span><span class="sxs-lookup"><span data-stu-id="02bb8-113">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="02bb8-114">Bu iki istemci sınıfı, bağlantının ayrıntılarını işleyebilmeniz gerekmeden TCP ve UDP yuvaları oluşturmayı kapsüller.</span><span class="sxs-lookup"><span data-stu-id="02bb8-114">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="02bb8-115">Kimlik bilgileri gerektiren sitelere erişirken, <xref:System.Net.CredentialCache> her istekte bunları sağlamak yerine, kimlik bilgilerinin bir önbelleğini oluşturmak için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="02bb8-115">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="02bb8-116">**CredentialCache** sınıfı, bir istekle birlikte sunmak üzere uygun kimlik bilgisini bulmak için önbelleği arar, bu da URL 'ye göre kimlik bilgileri oluşturma ve sunma sorumluluğunu ortadan kaldırmak.</span><span class="sxs-lookup"><span data-stu-id="02bb8-116">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02bb8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02bb8-117">See also</span></span>

- [<span data-ttu-id="02bb8-118">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="02bb8-118">Network Programming in the .NET Framework</span></span>](index.md)
