---
title: Temel ve Özet Kimlik Doğrulaması
description: Bir uygulamanın, veri istemek için kullandığı WebRequest nesnesinde bir Kullanıcı adı ve parola sağladığı temel ve Özet kimlik doğrulamasını kullanmayı öğrenin.
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
ms.openlocfilehash: 7772430b508b52a63d716550b69018385418c132
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502710"
---
# <a name="basic-and-digest-authentication"></a>Temel ve Özet Kimlik Doğrulaması
<xref:System.Net>Temel ve Özet kimlik doğrulamasının UYGULANMASı RFC2617 – http kimlik doğrulaması: temel ve Özet kimlik doğrulaması ( [World Wide Web Konsorsiyumu 'ın](https://www.w3.org) Web sitesinde bulunur) ile uyumludur.  
  
 Temel ve Özet kimlik doğrulamasını kullanmak için bir uygulamanın, <xref:System.Net.WebRequest.Credentials%2A> <xref:System.Net.WebRequest> Aşağıdaki örnekte gösterildiği gibi, Internet 'ten veri istemek için kullandığı nesnenin özelliğinde bir Kullanıcı adı ve parola sağlaması gerekir.  
  
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
