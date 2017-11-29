---
title: FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d7b169a6de494d10fa332ebf5f2aa315ae69653a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ftp"></a>FTP
.NET Framework, FTP Protokolü ile için kapsamlı destek sağlar. <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları. Bu sınıfların türetilmiş <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>. Çoğu durumda, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları isteği yapmak için gerekli olan tüm sağlar, ancak özellik olarak sunulan FTP özgü özellikler erişmesi gerekiyorsa, bu sınıfları typecast <xref:System.Net.FtpWebRequest> veya <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Örnekler  
 Daha fazla bilgi için aşağıdaki konulara bakın: [nasıl yapılır: dosyaları FTP ile](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [nasıl yapılır: FTP karşıya yükleme dosyalarıyla](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), ve [nasıl yapılır: FTP ile dizin içeriğini listele](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP ve proxy'ler  
 Bir proxy sunucu varsa (tarafından belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> özelliği) bir HTTP proxy yalnızca ise <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutları desteklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Proxy üzerinden Internet erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Ağ programlama örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [FTP istemcisi teknolojisi örnek](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [FTP Gezgini teknolojisi örneği](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [Uygulama protokolleri kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
