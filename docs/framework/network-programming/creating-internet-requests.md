---
title: İnternet İstekleri Oluşturma
description: Uygulamaların, kendisine geçirilen URI şemasını temel alan türetilmiş bir sınıf oluşturan WebRequest. Create yöntemi aracılığıyla WebRequest örnekleri oluşturma yöntemini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325633"
---
# <a name="create-internet-requests"></a><span data-ttu-id="0e0a1-103">İnternet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e0a1-103">Create internet requests</span></span>

<span data-ttu-id="0e0a1-104">Uygulamalar <xref:System.Net.WebRequest> , yöntemi aracılığıyla örnek oluşturur <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e0a1-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0e0a1-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>, <xref:System.Net.WebRequest> kendisine GEÇIRILEN URI şemasına göre türetilmiş bir sınıf oluşturan statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> is a static method that creates a class derived from <xref:System.Net.WebRequest> based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="0e0a1-106">Web, dosya ve FTP istekleri</span><span class="sxs-lookup"><span data-stu-id="0e0a1-106">Web, file, and FTP requests</span></span>

<span data-ttu-id="0e0a1-107">.NET Framework, <xref:System.Net.HttpWebRequest> `WebRequest` http ve https isteklerini işlemek için öğesinden türetilmiş sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-107">.NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from `WebRequest`, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="0e0a1-108">Çoğu durumda, `WebRequest` sınıfı bir istek yapmak için ihtiyacınız olan tüm özellikleri sağlar; ancak, gerekirse, `WebRequest` `WebRequest.Create` `HttpWebRequest` isteğin HTTP 'e özgü özelliklerine erişmek için yöntemi tarafından oluşturulan nesneleri türüne çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-108">In most cases, the `WebRequest` class provides all the properties you need to make a request; however, if necessary, you can cast `WebRequest` objects created by the `WebRequest.Create` method to the `HttpWebRequest` type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="0e0a1-109">Benzer şekilde, `HttpWebResponse` nesne http ve https isteklerindeki yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-109">Similarly, the `HttpWebResponse` object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="0e0a1-110">Nesnenin HTTP 'ye özgü özelliklerine erişmek için `HttpWebResponse` `WebResponse` nesneleri `HttpWebResponse` türe atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-110">To access the HTTP-specific properties of the `HttpWebResponse` object, you need to cast `WebResponse` objects to the `HttpWebResponse` type.</span></span>  
  
<span data-ttu-id="0e0a1-111">.NET Framework Ayrıca, <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> "File:" URI düzenini kullanan kaynaklara yönelik istekleri işlemek için ve sınıflarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-111">.NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="0e0a1-112">Benzer şekilde, <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları "FTP:" düzenini kullanan kaynaklar için istekleri işlemek üzere sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="0e0a1-113">İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak için ise, `WebRequest.Create` isteğinizi yapmak için bir nesne elde etmek üzere yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-113">If your request is for a resource that uses any of these schemes, you can use the `WebRequest.Create` method to obtain an object with which to make your request.</span></span>  
  
<span data-ttu-id="0e0a1-114">Diğer uygulama düzeyi protokolleri kullanan istekleri işlemek için, ve ' den türetilen protokole özgü sınıflar uygulayın `WebRequest` `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="0e0a1-114">To handle requests that use other application-level protocols, implement protocol-specific classes derived from `WebRequest` and `WebResponse`.</span></span> <span data-ttu-id="0e0a1-115">Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="0e0a1-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0a1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e0a1-116">See also</span></span>

- [<span data-ttu-id="0e0a1-117">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="0e0a1-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="0e0a1-118">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="0e0a1-118">Requesting Data</span></span>](requesting-data.md)
