---
title: FTP - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642886"
---
# <a name="ftp"></a><span data-ttu-id="6cd5e-102">FTP</span><span class="sxs-lookup"><span data-stu-id="6cd5e-102">FTP</span></span>

<span data-ttu-id="6cd5e-103">.NET Framework, FTP protokolü için <xref:System.Net.FtpWebRequest> sınıflarla <xref:System.Net.FtpWebResponse> kapsamlı bir destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6cd5e-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="6cd5e-104">Bu sınıflar türetilmiştir <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="6cd5e-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="6cd5e-105">Çoğu durumda, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar istekte bulunmak için gerekli olan her şeyi sağlar, ancak özellik olarak açıkta ftp'ye <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse>özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları veya .</span><span class="sxs-lookup"><span data-stu-id="6cd5e-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="6cd5e-106">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6cd5e-106">Examples</span></span>

<span data-ttu-id="6cd5e-107">Daha fazla bilgi için aşağıdaki konulara bakın: [FTP ile Dosyaları Nasıl İndirin,](how-to-download-files-with-ftp.md) [Nasıl İndirilir: FTP ile Dosya Yükleme](how-to-upload-files-with-ftp.md), ve [Nasıl: FTP ile Dizin İçerikleri Listele](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="6cd5e-107">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="6cd5e-108">FTP ve vekiller</span><span class="sxs-lookup"><span data-stu-id="6cd5e-108">FTP and proxies</span></span>

<span data-ttu-id="6cd5e-109"><xref:System.Net.FtpWebRequest.Proxy%2A> Bir proxy (özellik tarafından belirtilen) bir HTTP proxy <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>ise, <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> o zaman sadece , ve komutları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6cd5e-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cd5e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cd5e-110">See also</span></span>

- [<span data-ttu-id="6cd5e-111">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="6cd5e-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="6cd5e-112">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="6cd5e-112">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="6cd5e-113">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="6cd5e-113">Using Application Protocols</span></span>](using-application-protocols.md)
