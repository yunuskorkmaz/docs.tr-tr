---
title: FTP-.NET
description: .NET Framework FTP protokolü için, FtpWebRequest ve FtpWebResponse sınıflarını kullanarak sağladığı kapsamlı destek hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d21ca43cd1041df358dc5e2add9560fb33e85d83
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502593"
---
# <a name="ftp"></a><span data-ttu-id="ae99e-103">FTP</span><span class="sxs-lookup"><span data-stu-id="ae99e-103">FTP</span></span>

<span data-ttu-id="ae99e-104">.NET Framework, ve sınıflarıyla FTP protokolü için kapsamlı destek sağlar <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> .</span><span class="sxs-lookup"><span data-stu-id="ae99e-104">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="ae99e-105">Bu sınıflar <xref:System.Net.WebRequest> ve ' den türetilir <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="ae99e-105">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="ae99e-106">Çoğu durumda, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları isteği yapmak için gereken tüm öğeleri sağlar, ancak özellik olarak sunulan FTP 'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları veya olarak yazabilirsiniz <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> .</span><span class="sxs-lookup"><span data-stu-id="ae99e-106">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="ae99e-107">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ae99e-107">Examples</span></span>

<span data-ttu-id="ae99e-108">Daha fazla bilgi için şu konulara bakın: [nasıl yapılır: FTP Ile dosya indirme](how-to-download-files-with-ftp.md), [nasıl yapılır: FTP ile dosya](how-to-upload-files-with-ftp.md)yükleme ve [nasıl yapılır: FTP ile dizin içeriğini listeleme](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="ae99e-108">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="ae99e-109">FTP ve proxy 'ler</span><span class="sxs-lookup"><span data-stu-id="ae99e-109">FTP and proxies</span></span>

<span data-ttu-id="ae99e-110">Bir ara sunucu (özelliği ile belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> ) BIR http proxy 'si ise, yalnızca, <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae99e-110">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae99e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae99e-111">See also</span></span>

- [<span data-ttu-id="ae99e-112">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="ae99e-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="ae99e-113">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ae99e-113">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="ae99e-114">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="ae99e-114">Using Application Protocols</span></span>](using-application-protocols.md)
