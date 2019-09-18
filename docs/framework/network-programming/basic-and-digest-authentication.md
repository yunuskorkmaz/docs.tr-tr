---
title: Temel ve Özet Kimlik Doğrulaması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: 9a1ad701e1e8f4ee9966ebd56922c29e2bae7a03
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048907"
---
# <a name="basic-and-digest-authentication"></a>Temel ve Özet Kimlik Doğrulaması
Temel ve Özet kimlik doğrulamasının uygulanmasıRFC2617–httpkimlikdoğrulamasıileuyumludur:<xref:System.Net> Temel ve Özet kimlik doğrulaması ( [World Wide Web Konsorsiyumu](https://www.w3.org) Web sitesinde kullanılabilir).  
  
 Temel ve Özet kimlik doğrulamasını kullanmak için bir uygulamanın, aşağıdaki örnekte gösterildiği gibi, Internet 'ten veri <xref:System.Net.WebRequest.Credentials%2A> istemek için kullandığı <xref:System.Net.WebRequest> nesnenin özelliğinde bir Kullanıcı adı ve parola sağlaması gerekir.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
> Temel ve Özet kimlik doğrulamasıyla gönderilen veriler şifrelenmemiştir, bu nedenle veriler bir saldırgan tarafından görülebilir. Ayrıca, temel kimlik doğrulama kimlik bilgileri (Kullanıcı adı ve parola) açık olarak gönderilir ve yakalanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NTLM ve Kerberos Kimlik Doğrulaması](ntlm-and-kerberos-authentication.md)
- [İnternet Kimlik Doğrulaması](internet-authentication.md)
