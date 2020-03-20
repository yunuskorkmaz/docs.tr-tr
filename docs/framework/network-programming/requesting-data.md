---
title: Veri İsteme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
ms.openlocfilehash: 1f367caf7656a83597b6262a5746686df15d33b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047322"
---
# <a name="requesting-data"></a><span data-ttu-id="1317a-102">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="1317a-102">Requesting Data</span></span>
<span data-ttu-id="1317a-103">Günümüzün Internet'in dağıtılmış çalışma ortamında çalışan uygulamalar geliştirmek, her türlü kaynaktan veri almak için verimli ve kullanımı kolay bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1317a-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="1317a-104">Takılabilir protokoller, birden çok Internet protokolünden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="1317a-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="1317a-105">Bir Internet Sunucusundan Veri Yükleme ve İndirme</span><span class="sxs-lookup"><span data-stu-id="1317a-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="1317a-106">Basit istek ve yanıt <xref:System.Net.WebClient> işlemleri için sınıf, bir Internet sunucusuna veri yüklemek veya verileri indirmek için en kolay yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1317a-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="1317a-107">**WebClient,** dosyaları yüklemek ve indirmek, akış göndermek ve almak, sunucuya bir veri arabelleği göndermek ve yanıt almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1317a-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="1317a-108">**WebClient,** <xref:System.Net.WebRequest> Internet <xref:System.Net.WebResponse> kaynağına gerçek bağlantıları yapmak için sınıfları kullanır, böylece kayıtlı takılabilir protokol kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1317a-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="1317a-109">Daha karmaşık işlemler yapması gereken istemci **uygulamaları, WebRequest** sınıfını ve onun soyundan gelenleri kullanarak sunuculardan veri talep eder.</span><span class="sxs-lookup"><span data-stu-id="1317a-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="1317a-110">**WebRequest,** sunucuya bağlanma, isteği gönderme ve yanıt alma ayrıntılarını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="1317a-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="1317a-111">**WebRequest,** takılabilir protokoller kullanan tüm uygulamalar için kullanılabilen özellikler ve yöntemler kümesini tanımlayan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1317a-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="1317a-112">**WebRequest'in**torunları , <xref:System.Net.HttpWebRequest>örneğin, **WebRequest** tarafından tanımlanan özellikleri ve yöntemleri temel protokolle tutarlı bir şekilde uygularlar.</span><span class="sxs-lookup"><span data-stu-id="1317a-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="1317a-113">WebRequest sınıfı, oluşturmak için türetilmiş sınıf örneğini belirlemek için <xref:System.Net.WebRequest.Create%2A> yöntemine geçirilen URI değerini kullanarak **WebRequest** torunlarının protokole özgü örneklerini oluşturur. **WebRequest**</span><span class="sxs-lookup"><span data-stu-id="1317a-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="1317a-114">Uygulamalar, soyundan gelen oluşturucuyu <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemle kaydederek bir isteği işlemek için hangi **Webİstek** soyundan gelenin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1317a-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1317a-115"><xref:System.Net.WebRequest.GetResponse%2A> **WebRequest'teki**yöntemi arayarak Internet kaynağına istekte bulunular.</span><span class="sxs-lookup"><span data-stu-id="1317a-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="1317a-116">**GetResponse** **yöntemi, WebRequest'in**özelliklerinden protokole özgü isteği yapar, TCP veya UDP soketi bağlantısını sunucuya yapar ve isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="1317a-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="1317a-117">HTTP **Post** veya FTP **Put** istekleri gibi sunucuya veri <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> gönderen istekler için yöntem, verileri göndermek için bir ağ akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1317a-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="1317a-118">**GetResponse** yöntemi, **Webİsteği** ile eşleşen protokole özgü bir **WebResponse** döndürür.</span><span class="sxs-lookup"><span data-stu-id="1317a-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="1317a-119">**WebResponse** sınıfı aynı zamanda takılabilir protokolleri kullanan tüm uygulamalar için kullanılabilen özellikleri ve yöntemleri tanımlayan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1317a-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="1317a-120">**WebResponse** torunları, temel protokol için bu özellikleri ve yöntemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="1317a-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="1317a-121">Sınıf, <xref:System.Net.HttpWebResponse> örneğin, HTTP için **WebResponse** sınıfını uygular.</span><span class="sxs-lookup"><span data-stu-id="1317a-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="1317a-122">Sunucu tarafından döndürülen veriler <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemle döndürülen akıştaki uygulamaya sunulur.</span><span class="sxs-lookup"><span data-stu-id="1317a-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1317a-123">Aşağıdaki örnekte gösterildiği gibi, bu akışı diğerleri gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1317a-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="1317a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1317a-124">See also</span></span>

- [<span data-ttu-id="1317a-125">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="1317a-125">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="1317a-126">Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="1317a-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="1317a-127">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="1317a-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
