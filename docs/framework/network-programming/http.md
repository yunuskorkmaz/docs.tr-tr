---
title: HTTP
description: .NET Framework HttpWebRequest ve HttpWebResponse sınıflarını kullanarak sağladığı HTTP için kapsamlı destek hakkında bilgi edinin.
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
ms.openlocfilehash: ffb7a5d027ef7691d03caf0ac45d4a3dd9bdb652
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502424"
---
# <a name="http"></a><span data-ttu-id="6659d-103">HTTP</span><span class="sxs-lookup"><span data-stu-id="6659d-103">HTTP</span></span>
<span data-ttu-id="6659d-104">.NET Framework, ve sınıflarının yanı sıra tüm Internet trafiğinin çoğunu oluşturan HTTP protokolü için kapsamlı destek sağlar <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> .</span><span class="sxs-lookup"><span data-stu-id="6659d-104">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="6659d-105">Ve ' den türetilen bu sınıflar, <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> statik yöntem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> "http" veya "https" Ile başlayan bir URI ile karşılaştığında varsayılan olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6659d-105">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="6659d-106">Çoğu durumda, **WebRequest** ve **WebResponse** sınıfları isteği yapmak için gereken tüm öğeleri sağlar, ancak özellikler olarak sunulan http 'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları **HttpWebRequest** veya **HttpWebResponse**olarak yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6659d-106">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="6659d-107">**HttpWebRequest** ve **HttpWebResponse** standart bir http isteği-ve-yanıt işlemini kapsülle ve ortak http üst bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6659d-107">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="6659d-108">Bu sınıflar, ardışık düzen oluşturma, verileri parçalara gönderme ve alma, kimlik doğrulama, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifikası doğrulama ve bağlantı yönetimi dahil olmak üzere HTTP 1,1 özelliklerinin çoğunu da destekler.</span><span class="sxs-lookup"><span data-stu-id="6659d-108">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="6659d-109">Özellikler aracılığıyla sağlanmayan özel üstbilgiler ve üstbilgiler içinde depolanabilir ve **üstbilgiler** özelliği aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6659d-109">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="6659d-110">**HttpWebRequest** **WebRequest** tarafından kullanılan varsayılan sınıftır ve **WebRequest. Create** yöntemine bir URI geçirebilmeniz için önce kaydedilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6659d-110">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="6659d-111"><xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A>Özelliği **true** (varsayılan) olarak ayarlayarak uygulamanızın http yeniden yönlendirmelerini otomatik olarak izlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6659d-111">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="6659d-112">Uygulama istekleri yeniden yönlendirecektir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> **HttpWebResponse** özelliği, isteğe yanıt veren gerçek Web kaynağını içerir.</span><span class="sxs-lookup"><span data-stu-id="6659d-112">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="6659d-113">**Allowoto yeniden yönlendirme** 'yi **false**olarak ayarlarsanız uygulamanız http protokol hataları olarak yeniden yönlendirmeyi işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6659d-113">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="6659d-114">Uygulamalar, kümesi ile bir ile birleştirerek HTTP protokol hataları alır <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> <xref:System.Net.WebExceptionStatus> .</span><span class="sxs-lookup"><span data-stu-id="6659d-114">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="6659d-115"><xref:System.Net.WebException.Response%2A>Özelliği, sunucu tarafından gönderilen **WebResponse** 'u içerir ve karşılaşılan gerçek http hatası olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6659d-115">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6659d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6659d-116">See also</span></span>

- [<span data-ttu-id="6659d-117">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="6659d-117">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="6659d-118">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="6659d-118">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="6659d-119">Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="6659d-119">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
