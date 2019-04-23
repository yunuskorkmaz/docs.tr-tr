---
title: Takılabilir Protokoller Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: d14eb426c8e142f56d9f024dcbf37a1d2d78664d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072347"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="5076a-102">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="5076a-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="5076a-103">Özet <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları, takılabilir protokolleri temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="5076a-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="5076a-104">Protokole özgü sınıflarından türetme tarafından <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, bir uygulama bir Internet kaynağından veri istek ve yanıt kullanılan protokol belirtmeden okuyun.</span><span class="sxs-lookup"><span data-stu-id="5076a-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="5076a-105">Bir protokole özgü oluşturabilmeniz için önce <xref:System.Net.WebRequest>, kendi Create yöntemini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5076a-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="5076a-106">Statik <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> yöntemi <xref:System.Net.WebRequest> kaydetmek için bir <xref:System.Net.WebRequest> istekleri belirli bir Internet düzeni, bir şema ve sunucu için veya bir şema, sunucu ve yol için bir dizi işlemek için alt.</span><span class="sxs-lookup"><span data-stu-id="5076a-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="5076a-107">Çoğu durumda, yöntemlerini ve özelliklerini kullanarak veri göndermek ve almak mümkün olmayacak <xref:System.Net.WebRequest> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5076a-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="5076a-108">Ancak, protokole özgü özelliklere erişmek gereksinim duyarsanız, türü atayarak bir <xref:System.Net.WebRequest> belirli bir türetilmiş sınıf örneği.</span><span class="sxs-lookup"><span data-stu-id="5076a-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="5076a-109">Takılabilir protokoller yararlanmak için <xref:System.Net.WebRequest> alt öğeleri ayarlamak için protokole özgü özellikleri gerektirmeyen varsayılan bir istek ve yanıt işlem sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5076a-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="5076a-110">Örneğin, <xref:System.Net.HttpWebRequest> sınıfını <xref:System.Net.WebRequest> sağlar, HTTP için sınıf bir `GET` isteği varsayılan ve döndürür bir <xref:System.Net.HttpWebResponse> Web sunucusundan döndürülen akış içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5076a-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5076a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5076a-111">See also</span></span>

- [<span data-ttu-id="5076a-112">WebRequest’ten Türetme</span><span class="sxs-lookup"><span data-stu-id="5076a-112">Deriving from WebRequest</span></span>](../../../docs/framework/network-programming/deriving-from-webrequest.md)
- [<span data-ttu-id="5076a-113">WebResponse’tan Türetme</span><span class="sxs-lookup"><span data-stu-id="5076a-113">Deriving from WebResponse</span></span>](../../../docs/framework/network-programming/deriving-from-webresponse.md)
- [<span data-ttu-id="5076a-114">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="5076a-114">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="5076a-115">Nasıl yapılır: Protokole özgü özelliklere erişim WebRequest türü atayarak</span><span class="sxs-lookup"><span data-stu-id="5076a-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
