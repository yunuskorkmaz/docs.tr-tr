---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: 0f35cb5c106d041a771d17a6e528cbbc1d38042b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187679"
---
# <a name="ftp"></a><span data-ttu-id="ef249-102">FTP</span><span class="sxs-lookup"><span data-stu-id="ef249-102">FTP</span></span>
<span data-ttu-id="ef249-103">.NET Framework ile FTP protokolünü için kapsamlı destek sağlar. <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="ef249-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="ef249-104">Bu sınıflar türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="ef249-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="ef249-105">Çoğu durumda <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları istekte bulunmak gerekli olan tüm sağlar, ancak özellik olarak kullanıma FTP özgü özelliklere erişim gerekiyorsa, bu sınıflar için türü atayarak <xref:System.Net.FtpWebRequest> veya <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="ef249-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ef249-106">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ef249-106">Examples</span></span>  
 <span data-ttu-id="ef249-107">Daha fazla bilgi için aşağıdaki konulara bakın: [nasıl yapılır: FTP ile dosyaları](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [nasıl yapılır: FTP ile dosyaları karşıya yükle](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), ve [nasıl yapılır: FTP ile dizin içeriğini listeleme](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="ef249-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="ef249-108">FTP ve proxy'ler</span><span class="sxs-lookup"><span data-stu-id="ef249-108">FTP and proxies</span></span>  
 <span data-ttu-id="ef249-109">Bir proxy varsa (tarafından belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> özelliği) bir HTTP proxy'sinin yalnızca ise <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutlar desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ef249-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef249-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef249-110">See Also</span></span>  
 [<span data-ttu-id="ef249-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="ef249-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="ef249-112">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ef249-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="ef249-113">FTP istemcisi teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="ef249-113">FTP Client Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="ef249-114">FTP Gezgini teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="ef249-114">FTP Explorer Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="ef249-115">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef249-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
