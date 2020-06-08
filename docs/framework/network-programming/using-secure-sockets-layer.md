---
title: Güvenli Yuva Katmanı Kullanma
description: System.Net ve genişletme sınıflarının, .NET Framework çeşitli ağ protokolleri bağlantısını şifrelemek için Güvenli Yuva Katmanı nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 67330962382e768849cbf67d5f412ea80f65569d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501995"
---
# <a name="using-secure-sockets-layer"></a>Güvenli Yuva Katmanı Kullanma
<xref:System.Net>Sınıflar, birkaç ağ protokolünün bağlantısını şifrelemek için Güvenli Yuva Katmanı (SSL) kullanır.  
  
 Http bağlantılarında, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları SSL 'yi destekleyen Web Konakları ile iletişim kurmak için SSL kullanır. SSL kullanma kararı, <xref:System.Net.WebRequest> VERILEN URI temel alınarak sınıfı tarafından yapılır. URI "https:" ile başlıyorsa, SSL kullanılır; URI "http:" ile başlıyorsa, şifrelenmemiş bir bağlantı kullanılır.  
  
 SSL 'yi Dosya Aktarım Protokolü (FTP) ile birlikte kullanmak için, <xref:System.Net.FtpWebRequest.EnableSsl> çağrılmadan önce özelliği true olarak ayarlayın <xref:System.Net.FtpWebRequest.GetResponse> . Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) ile SSL kullanmak için, <xref:System.Net.Mail.SmtpClient.EnableSsl> e-postayı göndermeden önce özelliğini doğru olarak ayarlayın.  
  
 <xref:System.Net.Security.SslStream>Sınıfı, SSL için akış tabanlı bir soyutlama sağlar ve SSL anlaşmasını yapılandırmak için birçok yol sunar.  
  
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
 Bu örnek şunları gerektirir:  
  
- **System.net** ad alanına başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Güvenliği](security-in-network-programming.md)
- [.NET Framework'te Ağ Programlaması](index.md)
- [Sertifika Seçimi ve Doğrulama](certificate-selection-and-validation.md)
