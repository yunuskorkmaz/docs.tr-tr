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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047322"
---
# <a name="requesting-data"></a><span data-ttu-id="3ac54-102">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="3ac54-102">Requesting Data</span></span>
<span data-ttu-id="3ac54-103">Günümüzde Internet 'in dağıtılmış işletim ortamında çalışan uygulamaların geliştirilmesi, her türden kaynaktan veri almak için verimli ve kullanımı kolay bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3ac54-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="3ac54-104">Takılabilir protokoller, birden çok Internet protokolünden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ac54-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="3ac54-105">Internet sunucusundan verileri karşıya yükleme ve Indirme</span><span class="sxs-lookup"><span data-stu-id="3ac54-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="3ac54-106">Basit istek ve yanıt işlemleri için, <xref:System.Net.WebClient> sınıfı Internet sunucusuna veri yüklemek veya verileri indirmek için en kolay yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ac54-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="3ac54-107">**WebClient** , dosyaları karşıya yükleme ve indirme, akışları gönderme ve alma, bir veri arabelleğini sunucuya gönderme ve yanıt alma için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ac54-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="3ac54-108">**WebClient** , <xref:System.Net.WebRequest> Internet kaynağına <xref:System.Net.WebResponse> yapılan gerçek bağlantıları oluşturmak için ve sınıflarını kullanır, bu nedenle tüm kayıtlı takılabilir protokolleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ac54-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="3ac54-109">**WebRequest** sınıfını ve alt öğelerini kullanarak sunuculardan daha karmaşık işlemler yapması gereken istemci uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="3ac54-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="3ac54-110">**WebRequest** , sunucuya bağlanma, isteği gönderme ve yanıtı alma ayrıntılarını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="3ac54-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="3ac54-111">**WebRequest** , takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir olan özellikler ve yöntemler kümesini tanımlayan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="3ac54-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="3ac54-112">**WebRequest** <xref:System.Net.HttpWebRequest>'in (gibi) alt öğeleri, **WebRequest** tarafından tanımlanan özellikleri ve yöntemleri temel protokolle tutarlı bir şekilde uygular.</span><span class="sxs-lookup"><span data-stu-id="3ac54-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="3ac54-113">**WebRequest** sınıfı, oluşturulacak özel türetilmiş sınıf örneğini tespit etmek üzere yöntemine geçirilen URI değerini kullanarak **WebRequest** alt <xref:System.Net.WebRequest.Create%2A> öğelerinin protokolüne özgü örneklerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ac54-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="3ac54-114">Uygulamalar, alt öğe oluşturucusunu <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemiyle kaydederek bir isteği işlemek için hangi **WebRequest** alt öğesinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ac54-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3ac54-115"><xref:System.Net.WebRequest.GetResponse%2A> **Web isteğindeki**yöntemi çağırarak Internet kaynağına bir istek yapılır.</span><span class="sxs-lookup"><span data-stu-id="3ac54-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="3ac54-116">**GetResponse** yöntemi **WebRequest**özelliklerinden protokolüne özgü isteği oluşturur, TCP veya UDP soket bağlantısını sunucuya yapar ve isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="3ac54-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="3ac54-117">HTTP **Post** veya FTP **PUT** <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> istekleri gibi sunucuya veri gönderen isteklerde, yöntemi verilerin gönderileceği bir ağ akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ac54-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="3ac54-118">**GetResponse** yöntemi **WebRequest** ile eşleşen protokole özgü bir **WebResponse** döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ac54-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="3ac54-119">**WebResponse** sınıfı ayrıca takılabilir protokolleri kullanan tüm uygulamalar için kullanılabilen özellikleri ve yöntemleri tanımlayan bir soyut sınıftır.</span><span class="sxs-lookup"><span data-stu-id="3ac54-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="3ac54-120">**WebResponse** alt öğeleri, temel alınan protokol için bu özellikleri ve yöntemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="3ac54-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="3ac54-121">Sınıfı, örneğin, http için WebResponse sınıfını uygular. <xref:System.Net.HttpWebResponse></span><span class="sxs-lookup"><span data-stu-id="3ac54-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="3ac54-122">Sunucu tarafından döndürülen veriler, <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen akıştaki uygulamaya sunulur.</span><span class="sxs-lookup"><span data-stu-id="3ac54-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3ac54-123">Bu akışı, aşağıdaki örnekte gösterildiği gibi herhangi bir gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ac54-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ac54-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ac54-124">See also</span></span>

- [<span data-ttu-id="3ac54-125">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="3ac54-125">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="3ac54-126">Nasıl yapılır: Web sayfası isteme ve sonuçları akış olarak alma</span><span class="sxs-lookup"><span data-stu-id="3ac54-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="3ac54-127">Nasıl yapılır: WebRequest Ile eşleşen protokole özgü bir WebResponse alma</span><span class="sxs-lookup"><span data-stu-id="3ac54-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
