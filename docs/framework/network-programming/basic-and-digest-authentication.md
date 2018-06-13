---
title: Temel ve Özet kimlik doğrulaması
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fc061065caa4dad878a2a9b45e98ecb0d419d18b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398228"
---
# <a name="basic-and-digest-authentication"></a>Temel ve Özet kimlik doğrulaması
<xref:System.Net> Basic uygulamasıdır ve Özet kimlik doğrulaması RFC2617 – HTTP kimlik doğrulaması uyumludur: temel ve Özet kimlik doğrulaması (www.w3.org adresindeki World Wide Web Konsorsiyumu'nın Web sitesinde kullanılabilir).  
  
 Özet kimlik doğrulaması ve temel kullanmak için bir uygulama bir kullanıcı adı ve parola sağlamalısınız <xref:System.Net.WebRequest.Credentials%2A> özelliği <xref:System.Net.WebRequest> aşağıdaki örnekte gösterildiği gibi Internet'ten veri istemek için kullandığı nesne.  
  
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
>  Verileri bir saldırganın tarafından görülebilir için temel ve Özet kimlik doğrulaması ile gönderilen veriler şifrelenmez. Ayrıca, temel kimlik doğrulaması kimlik bilgilerini (kullanıcı adı ve parola) açık bir şekilde gönderilir ve geçirilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [NTLM ve Kerberos Kimlik Doğrulaması](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [İnternet Kimlik Doğrulaması](../../../docs/framework/network-programming/internet-authentication.md)
