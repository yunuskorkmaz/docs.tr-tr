---
title: "Temel ve Özet kimlik doğrulaması"
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a72635cb77f23e2b87abb54f3f6a4438a3019f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [NTLM ve Kerberos kimlik doğrulaması](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Internet kimlik doğrulama](../../../docs/framework/network-programming/internet-authentication.md)
