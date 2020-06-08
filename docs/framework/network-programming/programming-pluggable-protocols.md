---
title: Takılabilir Protokoller Programlama
description: Soyut WebRequest ve WebResponse sınıflarının, bir uygulamanın protokol belirtmeden veri almasını sağlayan takılabilir protokolleri nasıl desteklediğini öğrenin.
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
ms.openlocfilehash: 510f616295abc13d93e0e0af5a37aca097d343e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502203"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="27553-103">Takılabilir Protokoller Programlama</span><span class="sxs-lookup"><span data-stu-id="27553-103">Programming Pluggable Protocols</span></span>
<span data-ttu-id="27553-104">Soyut <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar takılabilir protokoller için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="27553-104">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="27553-105">Ve ' den protokolüne özgü sınıfları türeterek <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> , bir uygulama bir Internet kaynağından veri talep edebilir ve kullanılan protokolü belirtmeden yanıtı okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="27553-105">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="27553-106">Protokolüne özgü bir oluşturabilmeniz için önce <xref:System.Net.WebRequest> Create yöntemini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27553-106">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="27553-107"><xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> <xref:System.Net.WebRequest> Belirli bir Internet şemasına, bir düzene ve sunucuya ya da bir düzen, sunucu ve yol için bir istek kümesini işlemek üzere bir alt öğesi kaydetmek için ' ın statik metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="27553-107">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="27553-108">Çoğu durumda, sınıfının yöntemlerini ve özelliklerini kullanarak veri gönderebileceksiniz ve alabilirsiniz <xref:System.Net.WebRequest> .</span><span class="sxs-lookup"><span data-stu-id="27553-108">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="27553-109">Ancak, protokole özgü özelliklere erişmeniz gerekiyorsa, a 'yı <xref:System.Net.WebRequest> belirli bir türetilmiş sınıf örneğine yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27553-109">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="27553-110">Takılabilir protokollerinden yararlanmak için, alt bilgileriniz, <xref:System.Net.WebRequest> protokole özgü özelliklerin ayarlanmasına gerek olmayan varsayılan bir istek-yanıt işlemi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="27553-110">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="27553-111">Örneğin, <xref:System.Net.HttpWebRequest> <xref:System.Net.WebRequest> http için sınıfını uygulayan sınıfı, `GET` Varsayılan olarak bir Istek sağlar ve <xref:System.Net.HttpWebResponse> Web sunucusundan döndürülen akışı içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="27553-111">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27553-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27553-112">See also</span></span>

- [<span data-ttu-id="27553-113">WebRequest’ten Türetme</span><span class="sxs-lookup"><span data-stu-id="27553-113">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="27553-114">WebResponse’tan Türetme</span><span class="sxs-lookup"><span data-stu-id="27553-114">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="27553-115">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="27553-115">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="27553-116">Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="27553-116">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
