---
title: İnternet İstekleri Oluşturma
description: Uygulamaların, kendisine geçirilen URI şemasını temel alan türetilmiş bir sınıf oluşturan bir statik yöntem olan WebRequest. Create aracılığıyla Web Isteği örnekleri oluşturma hakkında bilgi edinin.
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
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502632"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="1bdf1-103">İnternet İstekleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bdf1-103">Creating Internet Requests</span></span>
<span data-ttu-id="1bdf1-104">Uygulamalar <xref:System.Net.WebRequest> , yöntemi aracılığıyla örnek oluşturur <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1bdf1-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1bdf1-105">Bu, kendisine geçirilen URI şemasını temel alan **WebRequest** 'ten türetilmiş bir sınıf oluşturan statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-105">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="1bdf1-106">Web, dosya ve FTP Istekleri</span><span class="sxs-lookup"><span data-stu-id="1bdf1-106">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="1bdf1-107">.NET Framework, <xref:System.Net.HttpWebRequest> http ve https isteklerini işlemek Için **WebRequest**'ten türetilen sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-107">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="1bdf1-108">Çoğu durumda, **WebRequest** sınıfı bir istek yapmak için ihtiyacınız olan tüm özellikleri sağlar; Ancak, gerekirse, isteğin HTTP 'e özgü özelliklerine erişmek için **Web isteği. Create** yöntemi tarafından oluşturulan **WebRequest** nesnelerini **HttpWebRequest** türüne çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-108">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="1bdf1-109">Benzer şekilde, **HttpWebResponse** nesnesi http ve https isteklerindeki yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-109">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="1bdf1-110">**HttpWebResponse** nesnesinin http 'e özgü özelliklerine erişmek Için **WebResponse** nesnelerini **HttpWebResponse** türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-110">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="1bdf1-111">.NET Framework Ayrıca, <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> "File:" URI düzenini kullanan kaynaklara yönelik istekleri işlemek için ve sınıflarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-111">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="1bdf1-112">Benzer şekilde, <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları "FTP:" düzenini kullanan kaynaklar için istekleri işlemek üzere sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="1bdf1-113">İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak için ise, isteğinizi yapmak için bir nesne elde etmek üzere **WebRequest. Create** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-113">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="1bdf1-114">Diğer uygulama düzeyi protokolleri kullanan istekleri işlemek için **WebRequest** ve **WebResponse**'dan türetilmiş protokole özgü sınıfları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-114">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="1bdf1-115">Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="1bdf1-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdf1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bdf1-116">See also</span></span>

- [<span data-ttu-id="1bdf1-117">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="1bdf1-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="1bdf1-118">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="1bdf1-118">Requesting Data</span></span>](requesting-data.md)
