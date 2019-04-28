---
title: FTP - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642886"
---
# <a name="ftp"></a><span data-ttu-id="5a607-102">FTP</span><span class="sxs-lookup"><span data-stu-id="5a607-102">FTP</span></span>

<span data-ttu-id="5a607-103">.NET Framework ile FTP protokolünü için kapsamlı destek sağlar. <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="5a607-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="5a607-104">Bu sınıflar türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="5a607-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="5a607-105">Çoğu durumda <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları istekte bulunmak gerekli olan tüm sağlar, ancak özellik olarak kullanıma FTP özgü özelliklere erişim gerekiyorsa, bu sınıflar için türü atayarak <xref:System.Net.FtpWebRequest> veya <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="5a607-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="5a607-106">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5a607-106">Examples</span></span>

<span data-ttu-id="5a607-107">Daha fazla bilgi için aşağıdaki konulara bakın: [Nasıl yapılır: FTP ile dosya indirme](how-to-download-files-with-ftp.md), [nasıl yapılır: FTP ile dosyaları karşıya yükleme](how-to-upload-files-with-ftp.md), ve [nasıl yapılır: FTP ile dizin içeriğini listeleme](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="5a607-107">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="5a607-108">FTP ve proxy'ler</span><span class="sxs-lookup"><span data-stu-id="5a607-108">FTP and proxies</span></span>

<span data-ttu-id="5a607-109">Bir proxy varsa (tarafından belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> özelliği) bir HTTP proxy'sinin yalnızca ise <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutlar desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5a607-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a607-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a607-110">See also</span></span>

- [<span data-ttu-id="5a607-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="5a607-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="5a607-112">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="5a607-112">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="5a607-113">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="5a607-113">Using Application Protocols</span></span>](using-application-protocols.md)
