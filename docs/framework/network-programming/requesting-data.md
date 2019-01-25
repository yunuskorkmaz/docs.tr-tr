---
title: Veri isteme
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
ms.openlocfilehash: 8e469e5480bbec8a04dbf280d4698acd5b328d72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678492"
---
# <a name="requesting-data"></a><span data-ttu-id="af90a-102">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="af90a-102">Requesting Data</span></span>
<span data-ttu-id="af90a-103">Günümüzün Internet dağıtılmış işletim ortamında çalışan uygulamalar geliştirme, her türden kaynaklardan veri almak için verimli, kullanımı kolay bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="af90a-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="af90a-104">Takılabilir protokoller birden çok Internet protokollerinden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="af90a-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="af90a-105">Karşıya yükleme ve bir Internet sunucusundan veri indirme</span><span class="sxs-lookup"><span data-stu-id="af90a-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="af90a-106">Basit isteği ve yanıt işlemleri <xref:System.Net.WebClient> sınıf verileri karşıya yükleme veya bir Internet sunucusundan verileri indirmek için kolay bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="af90a-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="af90a-107">**WebClient** dosyaları karşıya yükleme ve indirme, gönderme ve alma akışları ve bir veri arabelleği sunucuya göndermek ve bir yanıt almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="af90a-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="af90a-108">**WebClient** kullanan <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları, takılabilir Protokolü herhangi kayıtlı Internet kaynağına gerçek bağlantı olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af90a-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="af90a-109">Daha karmaşık işlem istek verileri kullanarak sunuculardan yapmanız istemci uygulamaları **WebRequest** sınıfı ve alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="af90a-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="af90a-110">**WebRequest** sunucuya bağlanırken, isteği gönderme ve yanıt alma ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="af90a-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="af90a-111">**WebRequest** özellikleri ve takılabilir protokoller kullanan tüm uygulamalar için kullanılabilen yöntemleri kümesini tanımlayan bir soyut sınıftır.</span><span class="sxs-lookup"><span data-stu-id="af90a-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="af90a-112">Alt öğeleri **WebRequest**, gibi <xref:System.Net.HttpWebRequest>, özellikleri ve yöntemleri tarafından tanımlanan uygulamak **WebRequest** temel alınan protokolü ile tutarlı bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="af90a-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="af90a-113">**WebRequest** sınıfı protokole özgü örneklerini oluşturur **WebRequest** URI değerini kullanarak alt öğeleri, geçirilen kendi <xref:System.Net.WebRequest.Create%2A> belirli türetilmiş sınıf belirlemek için yöntemi oluşturmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="af90a-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="af90a-114">Uygulamaları belirtin, **WebRequest** alt öğesi alt öğesi'nın oluşturucuyla kaydederek bir isteği işlemek için kullanılması gerekir <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af90a-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="af90a-115">İstek çağırarak Internet kaynağına yapılan <xref:System.Net.WebRequest.GetResponse%2A> metodunda **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="af90a-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="af90a-116">**GetResponse yanıtına** yöntemi oluşturur özelliklerini protokole özgü istekten **WebRequest**sunucusuna TCP veya UDP Yuva bağlantısı kurar ve isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="af90a-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="af90a-117">HTTP gibi sunucusuna veri gönderme istekleri **Post** veya FTP **Put** istekleri <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> yöntemi, veri göndermek bir ağ akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="af90a-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="af90a-118">**GetResponse yanıtına** yöntemi döndürür protokole özgü **WebResponse** eşleşen **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="af90a-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="af90a-119">**WebResponse** sınıfı, ayrıca bir soyut sınıf özellikleri ve takılabilir protokoller kullanan tüm uygulamalar için kullanılabilen yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af90a-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="af90a-120">**Webresponse'tan** alt öğeleri, bu özellikleri ve yöntemleri için temel alınan protokoldeki uygulayın.</span><span class="sxs-lookup"><span data-stu-id="af90a-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="af90a-121"><xref:System.Net.HttpWebResponse> Gibi uygulayan sınıf **WebResponse** HTTP için sınıf.</span><span class="sxs-lookup"><span data-stu-id="af90a-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="af90a-122">Sunucu tarafından döndürülen verilerin uygulama tarafından döndürülen akış içinde sunulan <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af90a-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="af90a-123">Aşağıdaki örnekte gösterildiği gibi diğer, bu akış kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af90a-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="af90a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af90a-124">See also</span></span>
- [<span data-ttu-id="af90a-125">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="af90a-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="af90a-126">Nasıl yapılır: Web sayfası isteme ve sonuçları bir Stream alma</span><span class="sxs-lookup"><span data-stu-id="af90a-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="af90a-127">Nasıl yapılır: WebRequest ile eşleşen protokole özgü WebResponse alma</span><span class="sxs-lookup"><span data-stu-id="af90a-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
