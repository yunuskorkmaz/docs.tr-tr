---
title: HTTP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: c8c799a50e5d63bbf411c338eb9e93f85a942bb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048006"
---
# <a name="http"></a><span data-ttu-id="b539b-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="b539b-102">HTTP</span></span>
<span data-ttu-id="b539b-103">.NET Framework, tüm Internet trafiğinin <xref:System.Net.HttpWebRequest> çoğunluğunu oluşturan HTTP protokolü için kapsamlı <xref:System.Net.HttpWebResponse> bir destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b539b-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="b539b-104">Statik yöntem <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> "http" veya "https" ile başlayan bir URI ile karşılaştığında, türetilen ve ,, varsayılan olarak döndürülen bu sınıflar.</span><span class="sxs-lookup"><span data-stu-id="b539b-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="b539b-105">Çoğu durumda, **Webİstek** ve **WebResponse** sınıfları isteği gerçekleştirmek için gerekli olan her şeyi sağlar, ancak özellikleri olarak açığa çıkarılan HTTP'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları **HttpWebRequest** veya **HttpWebResponse**adresine yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b539b-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="b539b-106">**HttpWebRequest** ve **HttpWebResponse** standart bir HTTP istek ve yanıt hareketi kapsüllemek ve ortak HTTP üstbilgi erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b539b-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="b539b-107">Bu sınıflar ayrıca pipelining, yığınlar halinde veri gönderme ve alma, kimlik doğrulama, ön authentication, şifreleme, proxy desteği, sunucu sertifikası doğrulama ve bağlantı yönetimi dahil olmak üzere çoğu HTTP 1.1 özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="b539b-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="b539b-108">Özellikler aracılığıyla sağlanmayan özel üstbilgi ve üstbilgi **üstbilgi** üstbilgi özelliği nden depolanabilir ve erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b539b-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="b539b-109">**HttpWebRequest,** **WebRequest** tarafından kullanılan varsayılan sınıftır ve Bir URI'yi **WebRequest.Create** yöntemine geçirmeden önce kaydedilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b539b-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="b539b-110"><xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> Uygulamanızın, özelliği **doğru** (varsayılan) olarak ayarlayarak HTTP yönlendirmelerini otomatik olarak izlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b539b-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="b539b-111">Uygulama istekleri yeniden yönlendirir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> **HttpWebResponse** özelliği isteğe yanıt veren gerçek Web kaynağını içerir.</span><span class="sxs-lookup"><span data-stu-id="b539b-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="b539b-112">**AllowAutoRedirect'i** **false**olarak ayarlarsanız, uygulamanız yönlendirmeleri HTTP iletişim kuralı hataları olarak işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b539b-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="b539b-113">Uygulamalar için <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> ayarlanmış bir yakalayarak HTTP <xref:System.Net.WebExceptionStatus>protokol hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b539b-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="b539b-114">Özellik, <xref:System.Net.WebException.Response%2A> sunucu tarafından gönderilen **WebYanıt'ı** içerir ve karşılaşılan gerçek HTTP hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b539b-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b539b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b539b-115">See also</span></span>

- [<span data-ttu-id="b539b-116">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="b539b-116">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="b539b-117">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="b539b-117">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="b539b-118">Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="b539b-118">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
