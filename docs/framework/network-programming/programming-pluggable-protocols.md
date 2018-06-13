---
title: Programlama takılabilir protokolleri
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fe9f9216c00448391967b82c84207f95eaccdb53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396151"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="3a15d-102">Programlama takılabilir protokolleri</span><span class="sxs-lookup"><span data-stu-id="3a15d-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="3a15d-103">Özet <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları takılabilir protokoller için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a15d-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="3a15d-104">Protokole özgü sınıflarından türetme tarafından <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, bir uygulama bir Internet kaynağından veri istek ve yanıt kullanılan protokolü belirtmeden okuyun.</span><span class="sxs-lookup"><span data-stu-id="3a15d-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="3a15d-105">Bir protokole özgü oluşturabilmeniz için önce <xref:System.Net.WebRequest>, Create yöntemini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a15d-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="3a15d-106">Statik kullanmak <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> yöntemi <xref:System.Net.WebRequest> kaydetmek için bir <xref:System.Net.WebRequest> isteklerini belirli bir Internet düzeni, bir şema ve sunucu için veya bir şema, sunucu ve yol için bir dizi işlemek için alt.</span><span class="sxs-lookup"><span data-stu-id="3a15d-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="3a15d-107">Çoğu durumda, özelliklerini ve yöntemlerini kullanarak veri gönderip kuramaz <xref:System.Net.WebRequest> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3a15d-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="3a15d-108">Ancak, protokole özgü özellikleri erişmeniz gerekiyorsa, typecast bir <xref:System.Net.WebRequest> belirli türetilmiş sınıf örneğinin.</span><span class="sxs-lookup"><span data-stu-id="3a15d-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="3a15d-109">Takılabilir Protokol yararlanmak için <xref:System.Net.WebRequest> descendants ayarlanacak özellikler protokole özgü gerektirmeyen bir varsayılan istek ve yanıt işlem sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a15d-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="3a15d-110">Örneğin, <xref:System.Net.HttpWebRequest> sınıfı, hangi uygular <xref:System.Net.WebRequest> sınıfı için HTTP, sağlar bir `GET` varsayılan ve döndürür isteğiyle bir <xref:System.Net.HttpWebResponse> Web sunucusundan döndürülen akış içerir.</span><span class="sxs-lookup"><span data-stu-id="3a15d-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a15d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a15d-111">See Also</span></span>  
 [<span data-ttu-id="3a15d-112">WebRequest’ten Türetme</span><span class="sxs-lookup"><span data-stu-id="3a15d-112">Deriving from WebRequest</span></span>](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [<span data-ttu-id="3a15d-113">WebResponse’tan Türetme</span><span class="sxs-lookup"><span data-stu-id="3a15d-113">Deriving from WebResponse</span></span>](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [<span data-ttu-id="3a15d-114">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="3a15d-114">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="3a15d-115">Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="3a15d-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
