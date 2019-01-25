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
ms.openlocfilehash: 2c764909514eac74cb930df055cdb846bab7b249
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502938"
---
# <a name="basic-and-digest-authentication"></a>Temel ve Özet kimlik doğrulama
<xref:System.Net> Uygulama temel ve Özet kimlik doğrulaması RFC2617 – HTTP kimlik doğrulaması ile uyumludur: Temel ve Özet kimlik doğrulaması (kullanılabilir [World Wide Web Consortium'ın](https://www.w3.org) Web sitesi).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [NTLM ve Kerberos Kimlik Doğrulaması](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [İnternet Kimlik Doğrulaması](../../../docs/framework/network-programming/internet-authentication.md)
