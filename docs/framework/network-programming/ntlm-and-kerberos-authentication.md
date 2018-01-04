---
title: "NTLM ve Kerberos kimlik doğrulaması"
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
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c1662e5b0f8afd4ef92d2893a11c25457dbce024
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ntlm-and-kerberos-authentication"></a>NTLM ve Kerberos kimlik doğrulaması
Varsayılan NTLM kimlik doğrulaması ve Kerberos kimlik doğrulaması sunucusu ile kimlik doğrulama denemesi için çağıran uygulama ile ilişkili Microsoft Windows NT kullanıcı kimlik bilgilerini kullanın. Varsayılan olmayan NTLM kimlik doğrulaması kullanırken, uygulama kimlik doğrulama türü NTLM olarak ayarlar ve kullandığı bir <xref:System.Net.NetworkCredential> kullanıcı adı, parola ve etki alanı aşağıdaki örnekte gösterildiği gibi ana bilgisayara geçirmek için nesne.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 Uygulama kullanıcı kimlik bilgilerini kullanarak Internet hizmetlerine bağlanmak için gereken uygulamalar aşağıdaki örnekte gösterildiği gibi kullanıcının varsayılan kimlik bilgileri ile bunu yapabilirsiniz.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 Anlaşma kimlik doğrulama modülü uzak sunucu NTLM veya Kerberos kimlik doğrulaması kullanıyor ve uygun yanıtı gönderen olup olmadığını belirler.  
  
> [!NOTE]
>  NTLM kimlik doğrulaması, bir proxy sunucu üzerinden çalışmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel ve Özet Kimlik Doğrulama](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [İnternet Kimlik Doğrulaması](../../../docs/framework/network-programming/internet-authentication.md)
