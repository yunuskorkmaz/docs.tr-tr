---
title: İnternet İstekleri Oluşturma
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
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048614"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="02419-102">İnternet İstekleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02419-102">Creating Internet Requests</span></span>
<span data-ttu-id="02419-103">Uygulamalar, <xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi aracılığıyla örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02419-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="02419-104">Bu, kendisine geçirilen URI şemasını temel alan **WebRequest** 'ten türetilmiş bir sınıf oluşturan statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="02419-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="02419-105">Web, dosya ve FTP Istekleri</span><span class="sxs-lookup"><span data-stu-id="02419-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="02419-106">.NET Framework, http ve <xref:System.Net.HttpWebRequest> https isteklerini işlemek için **WebRequest**'ten türetilen sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="02419-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="02419-107">Çoğu durumda, **WebRequest** sınıfı bir istek yapmak için ihtiyacınız olan tüm özellikleri sağlar; Ancak, gerekirse, isteğin HTTP 'e özgü özelliklerine erişmek için **Web isteği. Create** yöntemi tarafından oluşturulan **WebRequest** nesnelerini **HttpWebRequest** türüne çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02419-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="02419-108">Benzer şekilde, **HttpWebResponse** nesnesi http ve https isteklerindeki yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="02419-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="02419-109">**HttpWebResponse** nesnesinin http 'e özgü özelliklerine erişmek Için **WebResponse** nesnelerini **HttpWebResponse** türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="02419-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="02419-110">.NET Framework Ayrıca, "dosya <xref:System.Net.FileWebRequest> : <xref:System.Net.FileWebResponse> " kullanan kaynaklara yönelik istekleri işlemek için ve sınıflarını sağlar. URI şeması.</span><span class="sxs-lookup"><span data-stu-id="02419-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="02419-111">Benzer şekilde, <xref:System.Net.FtpWebResponse>vesınıfları "FTP:" düzenini kullanan kaynaklar için istekleri işlemek üzere sağlanır. <xref:System.Net.FtpWebRequest></span><span class="sxs-lookup"><span data-stu-id="02419-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="02419-112">İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak için ise, isteğinizi yapmak için bir nesne elde etmek üzere **WebRequest. Create** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02419-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="02419-113">Diğer uygulama düzeyi protokolleri kullanan istekleri işlemek için **WebRequest** ve **WebResponse**'dan türetilmiş protokole özgü sınıfları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="02419-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="02419-114">Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="02419-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02419-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02419-115">See also</span></span>

- [<span data-ttu-id="02419-116">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="02419-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="02419-117">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="02419-117">Requesting Data</span></span>](requesting-data.md)
