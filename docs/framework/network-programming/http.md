---
title: HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f72a77e19d04c0dd55887628033f7c975ac3ff25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="http"></a><span data-ttu-id="793b8-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="793b8-102">HTTP</span></span>
<span data-ttu-id="793b8-103">.NET Framework ile tüm Internet trafiğini çoğunluğu yapar HTTP protokolü için kapsamlı destek sağlar. <xref:System.Net.HttpWebRequest> ve <xref:System.Net.HttpWebResponse> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="793b8-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="793b8-104">Bu sınıfların türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, varsayılan olarak döndürülen her statik yöntemi <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> "http" veya "https" ile başlayan bir URI karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="793b8-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="793b8-105">Çoğu durumda, **WebRequest** ve **WebResponse** sınıfları sağlar, tüm istek yapılması gerekmez, ancak özellikleri olarak sunulan HTTP özgü özellikler erişmesi gerekiyorsa typecast Bu sınıfların **HttpWebRequest** veya **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="793b8-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="793b8-106">**HttpWebRequest** ve **HttpWebResponse** bir standart HTTP istek ve yanıt işlem kapsüllemek ve ortak HTTP üst bilgilerini erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="793b8-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="793b8-107">Bu sınıfları, ardışık düzen oluşturma, veri gönderip öbekleri, kimlik doğrulama, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifika doğrulaması ve bağlantı yönetimi dahil olmak üzere çoğu HTTP 1.1 özelliklerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="793b8-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="793b8-108">Özel üstbilgi ve özellikleri yoluyla sağlanmayan üstbilgileri içinde depolanabilir ve üzerinden erişilen **üstbilgileri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="793b8-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="793b8-109">**HttpWebRequest** tarafından kullanılan varsayılan sınıfı **WebRequest** ve URI'yı geçirmeden önce kaydedilmesi gerekmez **WebRequest.Create** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="793b8-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="793b8-110">HTTP yeniden yönlendirmeler otomatik olarak ayarlayarak izleyin, uygulamanızın yapabileceğiniz <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> özelliğine **true** (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="793b8-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="793b8-111">Uygulama istekleri yönlendirir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> özelliği **HttpWebResponse** isteğine yanıt gerçek Web kaynağına içerecektir.</span><span class="sxs-lookup"><span data-stu-id="793b8-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="793b8-112">Ayarlarsanız **AllowAutoRedirect** için **yanlış**, uygulamanızın yeniden yönlendirmeleri işleyebilen HTTP protokolü hata olarak.</span><span class="sxs-lookup"><span data-stu-id="793b8-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="793b8-113">Uygulamaları alma HTTP protokolü hatalarının yakalama tarafından bir <xref:System.Net.WebException> ile <xref:System.Net.WebException.Status%2A> kümesine <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="793b8-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="793b8-114"><xref:System.Net.WebException.Response%2A> Özelliği içeren **WebResponse** sunucu tarafından gönderilen ve karşılaşılan gerçek HTTP hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="793b8-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793b8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="793b8-115">See Also</span></span>  
 [<span data-ttu-id="793b8-116">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="793b8-116">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="793b8-117">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="793b8-117">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="793b8-118">Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="793b8-118">How to: Access HTTP-Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
