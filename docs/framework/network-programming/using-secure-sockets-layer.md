---
title: Güvenli Yuva Katmanı Kullanma
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
ms.openlocfilehash: ef2abc7574aea1b4f77ff93545ad84678c66ce48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046898"
---
# <a name="using-secure-sockets-layer"></a>Güvenli Yuva Katmanı Kullanma
Sınıflar, <xref:System.Net> çeşitli ağ protokolleri için bağlantıyı şifrelemek için Güvenli Soketkatmanını (SSL) kullanır.  
  
 Http bağlantıları için <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar, SSL'yi destekleyen web ana bilgisayarlarıyla iletişim kurmak için SSL'yi kullanır. SSL'yi kullanma kararı, <xref:System.Net.WebRequest> verilen URI'ye göre sınıf tarafından verilir. URI "https:" ile başlarsa, SSL kullanılır; URI "http:" ile başlarsa, şifrelenmemiş bir bağlantı kullanılır.  
  
 Dosya Aktarım Protokolü (FTP) ile SSL'yi kullanmak <xref:System.Net.FtpWebRequest.GetResponse>için, aramadan önce <xref:System.Net.FtpWebRequest.EnableSsl> özelliği doğru olarak ayarlayın. Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) <xref:System.Net.Mail.SmtpClient.EnableSsl> ile SSL kullanmak için, e-posta göndermeden önce gerçek özelliği ayarlayın.  
  
 Sınıf, <xref:System.Net.Security.SslStream> SSL için akış tabanlı bir soyutlama sağlar ve SSL el sıkışmasını yapılandırmanın birçok yolunu sunar.  
  
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
  
- **System.Net** ad alanına başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Güvenliği](security-in-network-programming.md)
- [.NET Framework'te Ağ Programlaması](index.md)
- [Sertifika Seçimi ve Doğrulama](certificate-selection-and-validation.md)
