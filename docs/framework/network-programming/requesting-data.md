---
title: İstekte bulunan verileri
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 166a076eae69b351248bc67570cdaf50b43ab95c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396304"
---
# <a name="requesting-data"></a><span data-ttu-id="ee015-102">İstekte bulunan verileri</span><span class="sxs-lookup"><span data-stu-id="ee015-102">Requesting Data</span></span>
<span data-ttu-id="ee015-103">Bugünün Internet dağıtılmış işletim ortamında çalışan uygulamalar geliştirme, tüm türleri kaynaklardan veri almak için verimli, kullanımı kolay bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ee015-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="ee015-104">Takılabilir Protokol birden çok Internet kurallarından veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ee015-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="ee015-105">Karşıya yükleme ve Internet sunucusundan veri indirme</span><span class="sxs-lookup"><span data-stu-id="ee015-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="ee015-106">Basit istek ve yanıt işlemler için <xref:System.Net.WebClient> sınıfı verileri yüklemeyi veya bir Internet sunucusundan veri indirmek için en kolay yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee015-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="ee015-107">**WebClient** karşıya yükleme ve indirme dosyaları, gönderme ve alma akışlar ve veri arabelleği sunucuya göndermek ve bir yanıt almak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee015-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="ee015-108">**WebClient** kullanan <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları herhangi takılabilir protokolü kayıtlı Internet kaynağının gerçek bağlantıları olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee015-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="ee015-109">Daha karmaşık işlemleri istek verileri kullanarak sunucularından yapmanız gereken istemci uygulamaları **WebRequest** sınıfı ve alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ee015-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="ee015-110">**WebRequest** bağlanırken, bu isteği göndermek ve yanıt alma ayrıntılarını yalıtır.</span><span class="sxs-lookup"><span data-stu-id="ee015-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="ee015-111">**WebRequest** özellikleri ve takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir yöntemleri kümesini tanımlayan bir Özet sınıf.</span><span class="sxs-lookup"><span data-stu-id="ee015-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="ee015-112">Alt öğeleri **WebRequest**, gibi <xref:System.Net.HttpWebRequest>, özellikleri ve yöntemleri tarafından tanımlanan uygulama **WebRequest** temel protokolü ile tutarlı bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="ee015-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="ee015-113">**WebRequest** sınıfı protokole özgü örneklerini oluşturur **WebRequest** URI değeri kullanılarak alt geçirilen kendi <xref:System.Net.WebRequest.Create%2A> belirli türetilmiş sınıf belirlemek amacıyla yöntemi oluşturmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="ee015-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="ee015-114">Uygulamaları belirtmek, **WebRequest** alt öğesi, alt öğesi'nin oluşturucusu ile kaydederek bir isteği işlemek için kullanılmalıdır <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee015-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ee015-115">Bir istek için Internet kaynağının çağırarak yapıldığında <xref:System.Net.WebRequest.GetResponse%2A> yöntemi **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="ee015-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="ee015-116">**GetResponse** yöntemi oluşturur özelliklerini protokole özgü isteğinden **WebRequest**, sunucuya TCP veya UDP yuva bağlantı yapar ve isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="ee015-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="ee015-117">HTTP gibi sunucusuna veri gönderme istekleri için **Post** veya FTP **Put** istekleri <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> yöntemi, veri göndermek bir ağ akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee015-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="ee015-118">**GetResponse** yöntemi döndürür protokole özgü **WebResponse** eşleşen **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="ee015-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="ee015-119">**WebResponse** sınıfı, ayrıca özellikleri ve takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir yöntemleri tanımlayan bir Özet sınıf.</span><span class="sxs-lookup"><span data-stu-id="ee015-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="ee015-120">**WebResponse** descendants uygulamak bu özellikleri ve yöntemleri temel protokolü için.</span><span class="sxs-lookup"><span data-stu-id="ee015-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="ee015-121"><xref:System.Net.HttpWebResponse> , Örneğin, uygulayan sınıf **WebResponse** HTTP için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ee015-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="ee015-122">Sunucu tarafından döndürülen veri tarafından döndürülen akış uygulamasına sunulan <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee015-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ee015-123">Aşağıdaki örnekte gösterildiği gibi diğer, bu akış kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee015-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee015-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee015-124">See Also</span></span>  
 [<span data-ttu-id="ee015-125">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="ee015-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="ee015-126">Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="ee015-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [<span data-ttu-id="ee015-127">Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma</span><span class="sxs-lookup"><span data-stu-id="ee015-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
