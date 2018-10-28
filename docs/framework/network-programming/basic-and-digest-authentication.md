---
title: Temel ve Özet kimlik doğrulama
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
ms.openlocfilehash: db39bdcaf2c3a4457028e30f9458a5626aa7e795
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190677"
---
# <a name="basic-and-digest-authentication"></a>Temel ve Özet kimlik doğrulama
<xref:System.Net> Uygulama temel ve Özet kimlik doğrulaması uyan RFC2617 – HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması (kullanılabilir [World Wide Web Consortium'ın](https://www.w3.org) Web sitesi).  
  
 Temel kullanmak ve Özet kimlik doğrulaması için bir uygulama bir kullanıcı adı ve parola sağlamalıdır <xref:System.Net.WebRequest.Credentials%2A> özelliği <xref:System.Net.WebRequest> , aşağıdaki örnekte gösterildiği gibi Internet'ten veri isteği için kullanılan nesne.  
  
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
>  Temel ve Özet kimlik doğrulaması ile gönderilen veriler şifrelenmez, bu şekilde verileri bir saldırgan tarafından görülebilir. Ayrıca, temel kimlik doğrulaması kimlik bilgilerini (kullanıcı adı ve parola) açık bir şekilde gönderilir ve kesilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [NTLM ve Kerberos Kimlik Doğrulaması](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [İnternet Kimlik Doğrulaması](../../../docs/framework/network-programming/internet-authentication.md)
