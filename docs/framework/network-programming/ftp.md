---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e491754b1c6c96e6afa9b172200cfb564307a8a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395081"
---
# <a name="ftp"></a>FTP
.NET Framework, FTP Protokolü ile için kapsamlı destek sağlar. <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları. Bu sınıfların türetilmiş <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>. Çoğu durumda, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları isteği yapmak için gerekli olan tüm sağlar, ancak özellik olarak sunulan FTP özgü özellikler erişmesi gerekiyorsa, bu sınıfları typecast <xref:System.Net.FtpWebRequest> veya <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Örnekler  
 Daha fazla bilgi için aşağıdaki konulara bakın: [nasıl yapılır: dosyaları FTP ile](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [nasıl yapılır: FTP karşıya yükleme dosyalarıyla](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), ve [nasıl yapılır: FTP ile dizin içeriğini listele](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP ve proxy'ler  
 Bir proxy sunucu varsa (tarafından belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> özelliği) bir HTTP proxy yalnızca ise <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutları desteklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ara Sunucu Üzerinden İnternet Erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [FTP istemcisi teknolojisi örnek](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [FTP Gezgini teknolojisi örneği](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
