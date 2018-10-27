---
title: Güvenli Yuva Katmanı kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: 41baeb9724d142bb860e51fa3ee84fb6c3f6261e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188696"
---
# <a name="using-secure-sockets-layer"></a>Güvenli Yuva Katmanı kullanma
<xref:System.Net> Sınıfları, çeşitli ağ protokolleri için bağlantıyı şifrelemek için Güvenli Yuva Katmanı (SSL) kullanın.  
  
 Http bağlantılarında <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları SSL destekleyen web konaklarla iletişim kurması için SSL kullanın. SSL karar tarafından yapılan <xref:System.Net.WebRequest> verilen URI üzerinde temel sınıf. URI ile başlıyorsa "https:", SSL kullanılır; URI ile başlıyorsa "http:", şifrelenmemiş bir bağlantı kullanılır.  
  
 Dosya Aktarım Protokolü (FTP) ile SSL kullanmak için ayarlanmış <xref:System.Net.FtpWebRequest.EnableSsl> özelliği true çağrılmadan önce <xref:System.Net.FtpWebRequest.GetResponse>. Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) ile SSL kullanmak için ayarlama <xref:System.Net.Mail.SmtpClient.EnableSsl> özelliğini e-postayı göndermeden önce true.  
  
 <xref:System.Net.Security.SslStream> Sınıfı için SSL akış tabanlı bir Özet sağlar ve SSL el sıkışması yapılandırmak için birçok yol sunar.  
  
## <a name="example"></a>Örnek  
  
### <a name="code"></a>Kod  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Başvurular **System.Net** ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Programlama Güvenliği](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)  
 [Sertifika Seçimi ve Doğrulama](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
