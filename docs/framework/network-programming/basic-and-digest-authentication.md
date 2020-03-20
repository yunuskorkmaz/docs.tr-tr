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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048907"
---
# <a name="basic-and-digest-authentication"></a>Temel ve Özet Kimlik Doğrulaması
Temel <xref:System.Net> ve özet kimlik doğrulamasının uygulanması RFC2617 – HTTP Kimlik Doğrulama: Temel ve Özet Kimlik Doğrulama [(World Wide Web Konsorsiyumu'nun](https://www.w3.org) web sitesinde mevcuttur) ile uyumludur.  
  
 Temel ve özet kimlik doğrulamasını kullanmak için, uygulamanın <xref:System.Net.WebRequest.Credentials%2A> aşağıdaki örnekte gösterildiği gibi, Internet'ten veri istemek için kullandığı <xref:System.Net.WebRequest> nesnenin özelliğinde bir kullanıcı adı ve parola sağlaması gerekir.  
  
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
> Temel ve Özet Kimlik Doğrulama ile gönderilen veriler şifrelenmez, bu nedenle veriler bir rakip tarafından görülebilir. Ayrıca, Temel Kimlik Doğrulama kimlik bilgileri (kullanıcı adı ve parola) açık olarak gönderilir ve ele geçirilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NTLM ve Kerberos Kimlik Doğrulaması](ntlm-and-kerberos-authentication.md)
- [İnternet Kimlik Doğrulaması](internet-authentication.md)
