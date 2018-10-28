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
