---
title: "Kullanarak Güvenli Yuva Katmanı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 31c8a3d22e6a7fa074eae18de8f9b2a9903457c1
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="using-secure-sockets-layer"></a>Kullanarak Güvenli Yuva Katmanı
<xref:System.Net> Sınıfları birkaç protokolleri ağ için bağlantıyı şifrelemek için Güvenli Yuva Katmanı (SSL) kullanın.  
  
 Http bağlantıları için <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflarını SSL desteği web ana bilgisayarlar ile iletişim kurmak için SSL kullanın. SSL kullanmak üzere kararı tarafından yapılan <xref:System.Net.WebRequest> , verilen URI temel sınıf. URI ile başlıyorsa "https:", SSL kullanılır; URI ile başlıyorsa "http:", şifrelenmemiş bir bağlantı kullanılır.  
  
 Dosya Aktarım Protokolü (FTP) ile SSL kullanmak üzere ayarlanmış <xref:System.Net.FtpWebRequest.EnableSsl> özelliğinin true çağrılmadan önce <xref:System.Net.FtpWebRequest.GetResponse>. Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) ile SSL kullanmak üzere ayarlanmış <xref:System.Net.Mail.SmtpClient.EnableSsl> özelliğinin e-postayı göndermeden önce true.  
  
 <xref:System.Net.Security.SslStream> Sınıfı için SSL akışı tabanlı bir Özet sağlar ve SSL el sıkışması yapılandırmak için birçok yol sunar.  
  
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
