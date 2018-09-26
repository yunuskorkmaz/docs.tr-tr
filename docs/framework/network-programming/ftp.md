---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 286ab6ad4742f3e31db8037e10e98d5890c6144d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200925"
---
# <a name="ftp"></a>FTP
.NET Framework ile FTP protokolünü için kapsamlı destek sağlar. <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları. Bu sınıflar türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>. Çoğu durumda <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları istekte bulunmak gerekli olan tüm sağlar, ancak özellik olarak kullanıma FTP özgü özelliklere erişim gerekiyorsa, bu sınıflar için türü atayarak <xref:System.Net.FtpWebRequest> veya <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Örnekler  
 Daha fazla bilgi için aşağıdaki konulara bakın: [nasıl yapılır: FTP ile dosyaları](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [nasıl yapılır: FTP ile dosyaları karşıya yükle](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), ve [nasıl yapılır: FTP ile dizin içeriğini listeleme](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP ve proxy'ler  
 Bir proxy varsa (tarafından belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> özelliği) bir HTTP proxy'sinin yalnızca ise <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutlar desteklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ara Sunucu Üzerinden İnternet Erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [FTP istemcisi teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [FTP Gezgini teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
