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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048614"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="c856f-102">İnternet İstekleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c856f-102">Creating Internet Requests</span></span>
<span data-ttu-id="c856f-103">Uygulamalar <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntem <xref:System.Net.WebRequest> üzerinden örnekler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c856f-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c856f-104">Bu, **webisteğinden** türetilen bir sınıfı, ona geçirilen URI düzenini temel alan statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c856f-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="c856f-105">Web, Dosya ve FTP İstekleri</span><span class="sxs-lookup"><span data-stu-id="c856f-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="c856f-106">.NET Framework, <xref:System.Net.HttpWebRequest> HTTP ve HTTPS isteklerini işlemek için **WebRequest'ten**türetilen sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c856f-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="c856f-107">Çoğu durumda, **Webİstek** sınıfı istekte bulunmak için gereken tüm özellikleri sağlar; ancak, gerekirse, isteğin HTTP'ye özgü özelliklerine erişmek için **WebRequest.Create** yöntemi tarafından oluşturulan **WebRequest** nesnelerini **HttpWebRequest** türüne atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c856f-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="c856f-108">Benzer şekilde, **HttpWebResponse** nesnesi HTTP ve HTTPS isteklerinden gelen yanıtları işler.</span><span class="sxs-lookup"><span data-stu-id="c856f-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="c856f-109">**HttpWebResponse** nesnesinin HTTP'ye özgü özelliklerine erişmek için **WebResponse** nesnelerini **HttpWebResponse** türüne dökmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c856f-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="c856f-110">.NET Framework ayrıca <xref:System.Net.FileWebRequest> "dosya:" URI düzenini kullanan kaynaklar için istekleri işlemek için <xref:System.Net.FileWebResponse> ve sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c856f-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="c856f-111">Aynı şekilde, <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> ve sınıflar "ftp:" düzenini kullanan kaynaklar için istekleri işlemek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c856f-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="c856f-112">İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak içinse, isteğinizi yapmak için bir nesne elde etmek için **WebRequest.Create** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c856f-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="c856f-113">Diğer uygulama düzeyi protokollerini kullanan istekleri işlemek için **WebRequest** ve **WebResponse'dan**türetilen protokole özgü sınıfları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c856f-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="c856f-114">Daha fazla bilgi için, [Takılabilir Programlama Protokolleri'ne](programming-pluggable-protocols.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c856f-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c856f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c856f-115">See also</span></span>

- [<span data-ttu-id="c856f-116">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="c856f-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="c856f-117">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="c856f-117">Requesting Data</span></span>](requesting-data.md)
