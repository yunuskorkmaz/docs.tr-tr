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
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047394"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="ef3e4-102">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="ef3e4-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="ef3e4-103">Soyut <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar takılabilir protokoller için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="ef3e4-104">Bir uygulama, protokole özgü <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>sınıfları bir Internet kaynağından veri isteyebilir ve kullanılan protokolü belirtmeden yanıtı okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="ef3e4-105">Protokole özgü <xref:System.Net.WebRequest>bir yöntem oluşturmadan önce, oluştur yöntemini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="ef3e4-106">Belirli bir <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> Internet <xref:System.Net.WebRequest> düzenine, bir düzene ve sunucuya veya bir şemaya, sunucuya ve yola bir dizi isteği işlemek için bir soyundan geleni <xref:System.Net.WebRequest> kaydetmek için statik yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="ef3e4-107">Çoğu <xref:System.Net.WebRequest> durumda, sınıfın yöntemlerini ve özelliklerini kullanarak veri gönderip alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="ef3e4-108">Ancak, protokole özgü özelliklere erişmeniz gerekiyorsa, <xref:System.Net.WebRequest> a'dan türemiş sınıf örneğine dakti-resmon yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="ef3e4-109">Takılabilir protokollerden yararlanmak için, <xref:System.Net.WebRequest> torunlarınızın protokole özgü özelliklerin ayarlanmasını gerektirmeyen varsayılan istek ve yanıt hareketi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="ef3e4-110">Örneğin, HTTP <xref:System.Net.HttpWebRequest> <xref:System.Net.WebRequest> için sınıfı uygulayan sınıf varsayılan olarak `GET` bir istek sağlar <xref:System.Net.HttpWebResponse> ve Web sunucusundan döndürülen akışı içeren bir istek verir.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3e4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef3e4-111">See also</span></span>

- [<span data-ttu-id="ef3e4-112">WebRequest’ten Türetme</span><span class="sxs-lookup"><span data-stu-id="ef3e4-112">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="ef3e4-113">WebResponse’tan Türetme</span><span class="sxs-lookup"><span data-stu-id="ef3e4-113">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="ef3e4-114">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="ef3e4-114">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="ef3e4-115">Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="ef3e4-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
