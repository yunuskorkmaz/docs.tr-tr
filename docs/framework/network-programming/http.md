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
ms.openlocfilehash: abbb02b7bd22c4b301c5565037f55aa1019fc3ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170605"
---
# <a name="http"></a><span data-ttu-id="04e08-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="04e08-102">HTTP</span></span>
<span data-ttu-id="04e08-103">.NET Framework ile tüm Internet trafiği, çoğu yapar HTTP protokolü için kapsamlı destek sağlar. <xref:System.Net.HttpWebRequest> ve <xref:System.Net.HttpWebResponse> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="04e08-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="04e08-104">Bu sınıflar türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, varsayılan olarak döndürülen her statik yöntem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> URI başlayan bir "http" veya "https" ile karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="04e08-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="04e08-105">Çoğu durumda **WebRequest** ve **WebResponse** sınıfları sağlar, tüm istek yapmak gerekli olduğu, ancak özellik olarak kullanıma HTTP'ye özgü özelliklere erişim gerekiyorsa, türü atayarak Bu sınıfa **HttpWebRequest** veya **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="04e08-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="04e08-106">**HttpWebRequest** ve **HttpWebResponse** standart bir HTTP istek ve yanıt hareket halinde kapsüller ve ortak HTTP üst bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="04e08-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="04e08-107">Bu sınıfların ardışık düzen, veri gönderip öbekleri, kimlik doğrulaması, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifika doğrulaması ve bağlantı yönetimi dahil olmak üzere çoğu HTTP 1.1 özelliklerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="04e08-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="04e08-108">Özel üst bilgiler özellikleri aracılığıyla sağlanmayan üst bilgiler depolanır ve aracılığıyla erişilen **üstbilgileri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="04e08-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="04e08-109">**HttpWebRequest** tarafından kullanılan varsayılan sınıf **WebRequest** ve bir URI geçirebilirsiniz önce kayıtlı olması gerekmez **WebRequest.Create** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04e08-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="04e08-110">HTTP yeniden yönlendirmelerini otomatik olarak ayarlayarak izleyin, uygulamanızın yapabileceğiniz <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> özelliğini **true** (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="04e08-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="04e08-111">Uygulama istekleri yönlendirir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> özelliği **HttpWebResponse** isteğine yanıt olarak verilen gerçek bir Web kaynağı içerir.</span><span class="sxs-lookup"><span data-stu-id="04e08-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="04e08-112">Ayarlarsanız **AllowAutoRedirect** için **false**, uygulamanızı yeniden yönlendirmeleri işleyebilen HTTP protokolü hata olarak.</span><span class="sxs-lookup"><span data-stu-id="04e08-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="04e08-113">Uygulamaları, yakalama tarafından HTTP protokolü hataları alan bir <xref:System.Net.WebException> ile <xref:System.Net.WebException.Status%2A> kümesine <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="04e08-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="04e08-114"><xref:System.Net.WebException.Response%2A> Özelliği içeren **WebResponse** sunucu tarafından gönderilen ve karşılaşılan gerçek HTTP hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="04e08-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e08-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04e08-115">See also</span></span>

- [<span data-ttu-id="04e08-116">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="04e08-116">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="04e08-117">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="04e08-117">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="04e08-118">Nasıl yapılır: HTTP'ye özgü özelliklere erişim</span><span class="sxs-lookup"><span data-stu-id="04e08-118">How to: Access HTTP-Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
