---
title: "Internet isteği oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8cbbb0db657f002c189ab4db9311ca48d83c32a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-internet-requests"></a><span data-ttu-id="7e70a-102">Internet isteği oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e70a-102">Creating Internet Requests</span></span>
<span data-ttu-id="7e70a-103">Uygulamaları oluşturma <xref:System.Net.WebRequest> aracılığıyla örnekleri <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7e70a-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7e70a-104">Bu, türetilmiş bir sınıf oluşturur, statik bir yöntemdir **WebRequest** kendisine geçirilen URI şeması göre.</span><span class="sxs-lookup"><span data-stu-id="7e70a-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="7e70a-105">Web, dosya ve FTP istekleri</span><span class="sxs-lookup"><span data-stu-id="7e70a-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="7e70a-106">.NET Framework sağlar <xref:System.Net.HttpWebRequest> türetilmiş sınıf **WebRequest**, HTTP ve HTTPS isteklerini işlemek için.</span><span class="sxs-lookup"><span data-stu-id="7e70a-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="7e70a-107">Çoğu durumda, **WebRequest** sınıfı, bir isteği yapmak için gereken tüm özellikleri sağlar; gerekirse, ancak çevirebilirsiniz **WebRequest** tarafından oluşturulan nesneler **WebRequest.Create**  yönteme **HttpWebRequest** isteğin HTTP özgü özelliklere erişmek için türü.</span><span class="sxs-lookup"><span data-stu-id="7e70a-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="7e70a-108">Benzer şekilde, **HttpWebResponse** nesne HTTP ve HTTPS istekleri yanıtlarının işler.</span><span class="sxs-lookup"><span data-stu-id="7e70a-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="7e70a-109">HTTP özgü özelliklerine erişmek için **HttpWebResponse** nesnesi, cast gereken **WebResponse** nesneleri **HttpWebResponse** türü.</span><span class="sxs-lookup"><span data-stu-id="7e70a-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="7e70a-110">.NET Framework ayrıca sağlar <xref:System.Net.FileWebRequest> ve <xref:System.Net.FileWebResponse> kullanan kaynaklar için istekleri işlemek için sınıflar "dosya:" URI düzeni.</span><span class="sxs-lookup"><span data-stu-id="7e70a-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="7e70a-111">Benzer şekilde, <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları kullanan kaynaklar için istekleri işlemek için sağlanan "ftp:" düzeni.</span><span class="sxs-lookup"><span data-stu-id="7e70a-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="7e70a-112">İsteğiniz bu düzenleri birini kullanan bir kaynak için ise, kullanabileceğiniz **WebRequest.Create** hangi isteğiniz yapmak bir nesne elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7e70a-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="7e70a-113">Diğer uygulama düzeyi protokolleri kullanan isteklerini işlemek için türetilmiş protokole özgü sınıflar uygulamanız gereken **WebRequest** ve **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="7e70a-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="7e70a-114">Daha fazla bilgi için bkz: [programlama Takılabilir Protokol](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="7e70a-114">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e70a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e70a-115">See Also</span></span>  
 [<span data-ttu-id="7e70a-116">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="7e70a-116">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [<span data-ttu-id="7e70a-117">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="7e70a-117">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
