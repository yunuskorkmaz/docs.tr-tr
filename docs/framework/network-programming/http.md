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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048006"
---
# <a name="http"></a><span data-ttu-id="eec4b-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="eec4b-102">HTTP</span></span>
<span data-ttu-id="eec4b-103">.NET Framework, <xref:System.Net.HttpWebRequest> ve <xref:System.Net.HttpWebResponse> sınıflarının yanı sıra tüm Internet trafiğinin çoğunu oluşturan http protokolü için kapsamlı destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="eec4b-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="eec4b-104">Ve <xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> ' den türetilen bu sınıflar, statik yöntem "http" veya "https" ile başlayan bir URI ile karşılaştığında varsayılan olarak döndürülür. <xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="eec4b-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="eec4b-105">Çoğu durumda, **WebRequest** ve **WebResponse** sınıfları isteği yapmak için gereken tüm öğeleri sağlar, ancak özellikler olarak sunulan http 'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları **HttpWebRequest** 'e yazabilirsiniz veya **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="eec4b-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="eec4b-106">**HttpWebRequest** ve **HttpWebResponse** standart bir http isteği-ve-yanıt işlemini kapsülle ve ortak http üst bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="eec4b-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="eec4b-107">Bu sınıflar, ardışık düzen oluşturma, verileri parçalara gönderme ve alma, kimlik doğrulama, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifikası doğrulama ve bağlantı yönetimi dahil olmak üzere HTTP 1,1 özelliklerinin çoğunu da destekler.</span><span class="sxs-lookup"><span data-stu-id="eec4b-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="eec4b-108">Özellikler aracılığıyla sağlanmayan özel üstbilgiler ve üstbilgiler içinde depolanabilir ve **üstbilgiler** özelliği aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="eec4b-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="eec4b-109">**HttpWebRequest** **WebRequest** tarafından kullanılan varsayılan sınıftır ve **WebRequest. Create** yöntemine bir URI geçirebilmeniz için önce kaydedilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eec4b-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="eec4b-110"><xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> Özelliği **true** (varsayılan) olarak ayarlayarak uygulamanızın http yeniden yönlendirmelerini otomatik olarak izlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec4b-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="eec4b-111">Uygulama istekleri yeniden yönlendirecektir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> **HttpWebResponse** özelliği, isteğe yanıt veren gerçek Web kaynağını içerir.</span><span class="sxs-lookup"><span data-stu-id="eec4b-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="eec4b-112">**Allowoto yeniden yönlendirme** 'yi **false**olarak ayarlarsanız uygulamanız http protokol hataları olarak yeniden yönlendirmeyi işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="eec4b-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="eec4b-113">Uygulamalar, <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> kümesi ilebirilebirleştirerekhttpprotokolhatalarıalır.<xref:System.Net.WebExceptionStatus></span><span class="sxs-lookup"><span data-stu-id="eec4b-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="eec4b-114">Özelliği, sunucu tarafından gönderilen WebResponse 'u içerir ve karşılaşılan gerçek http hatası olduğunu gösterir. <xref:System.Net.WebException.Response%2A></span><span class="sxs-lookup"><span data-stu-id="eec4b-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec4b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eec4b-115">See also</span></span>

- [<span data-ttu-id="eec4b-116">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="eec4b-116">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="eec4b-117">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="eec4b-117">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="eec4b-118">Nasıl yapılır: HTTP 'e özgü özelliklere erişin</span><span class="sxs-lookup"><span data-stu-id="eec4b-118">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
