---
title: Veri İsteme
description: Takılabilir protokollerin birden çok protokolden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize nasıl olanak sağladığını öğrenin.
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
ms.openlocfilehash: 19350d685a81d56657ca0a117d61b50ae24fab6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502190"
---
# <a name="requesting-data"></a><span data-ttu-id="ac4b0-103">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="ac4b0-103">Requesting Data</span></span>
<span data-ttu-id="ac4b0-104">Günümüzde Internet 'in dağıtılmış işletim ortamında çalışan uygulamaların geliştirilmesi, her türden kaynaktan veri almak için verimli ve kullanımı kolay bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-104">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="ac4b0-105">Takılabilir protokoller, birden çok Internet protokolünden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-105">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="ac4b0-106">Internet sunucusundan verileri karşıya yükleme ve Indirme</span><span class="sxs-lookup"><span data-stu-id="ac4b0-106">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="ac4b0-107">Basit istek ve yanıt işlemleri için, <xref:System.Net.WebClient> sınıfı Internet sunucusuna veri yüklemek veya verileri indirmek için en kolay yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-107">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="ac4b0-108">**WebClient** , dosyaları karşıya yükleme ve indirme, akışları gönderme ve alma, bir veri arabelleğini sunucuya gönderme ve yanıt alma için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-108">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="ac4b0-109">**WebClient** , <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> Internet kaynağına yapılan gerçek bağlantıları oluşturmak için ve sınıflarını kullanır, bu nedenle tüm kayıtlı takılabilir protokolleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-109">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="ac4b0-110">**WebRequest** sınıfını ve alt öğelerini kullanarak sunuculardan daha karmaşık işlemler yapması gereken istemci uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-110">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="ac4b0-111">**WebRequest** , sunucuya bağlanma, isteği gönderme ve yanıtı alma ayrıntılarını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-111">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="ac4b0-112">**WebRequest** , takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir olan özellikler ve yöntemler kümesini tanımlayan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-112">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="ac4b0-113">**WebRequest**'in (gibi) alt öğeleri, <xref:System.Net.HttpWebRequest> **WebRequest** tarafından tanımlanan özellikleri ve yöntemleri temel protokolle tutarlı bir şekilde uygular.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-113">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="ac4b0-114">**WebRequest** sınıfı, oluşturulacak özel türetilmiş sınıf örneğini tespit etmek üzere YÖNTEMINE geçirilen URI değerini kullanarak **WebRequest** alt öğelerinin protokolüne özgü örneklerini oluşturur <xref:System.Net.WebRequest.Create%2A> .</span><span class="sxs-lookup"><span data-stu-id="ac4b0-114">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="ac4b0-115">Uygulamalar, alt öğe oluşturucusunu yöntemiyle kaydederek bir isteği işlemek için hangi **WebRequest** alt öğesinin kullanılacağını belirtir <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ac4b0-115">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ac4b0-116"><xref:System.Net.WebRequest.GetResponse%2A> **Web isteğindeki**yöntemi çağırarak Internet kaynağına bir istek yapılır.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-116">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="ac4b0-117">**GetResponse** yöntemi **WebRequest**özelliklerinden protokolüne özgü isteği oluşturur, TCP veya UDP soket bağlantısını sunucuya yapar ve isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-117">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="ac4b0-118">HTTP **Post** veya FTP **PUT** istekleri gibi sunucuya veri gönderen isteklerde, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> yöntemi verilerin gönderileceği bir ağ akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-118">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="ac4b0-119">**GetResponse** yöntemi **WebRequest** ile eşleşen protokole özgü bir **WebResponse** döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-119">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="ac4b0-120">**WebResponse** sınıfı ayrıca takılabilir protokolleri kullanan tüm uygulamalar için kullanılabilen özellikleri ve yöntemleri tanımlayan bir soyut sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-120">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="ac4b0-121">**WebResponse** alt öğeleri, temel alınan protokol için bu özellikleri ve yöntemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-121">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="ac4b0-122"><xref:System.Net.HttpWebResponse>Sınıfı, örneğin, http Için **WebResponse** sınıfını uygular.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-122">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="ac4b0-123">Sunucu tarafından döndürülen veriler, yöntemi tarafından döndürülen akıştaki uygulamaya sunulur <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ac4b0-123">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ac4b0-124">Bu akışı, aşağıdaki örnekte gösterildiği gibi herhangi bir gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-124">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac4b0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac4b0-125">See also</span></span>

- [<span data-ttu-id="ac4b0-126">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="ac4b0-126">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="ac4b0-127">Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="ac4b0-127">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="ac4b0-128">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="ac4b0-128">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
