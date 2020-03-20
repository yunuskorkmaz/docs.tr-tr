---
title: NTLM ve Kerberos Kimlik Doğrulaması
ms.date: 03/30/2017
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
ms.openlocfilehash: 372101763bdd84b454e6e2db3ec6cf0ebdf3f991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180694"
---
# <a name="ntlm-and-kerberos-authentication"></a>NTLM ve Kerberos Kimlik Doğrulaması
Varsayılan NTLM kimlik doğrulaması ve Kerberos kimlik doğrulaması, sunucuyla kimlik doğrulamayı denemek için arama uygulamasıyla ilişkili Microsoft Windows NT kullanıcı kimlik bilgilerini kullanır. Varsayılan olmayan NTLM kimlik doğrulaması kullanırken, uygulama kimlik doğrulama türünü <xref:System.Net.NetworkCredential> NTLM olarak ayarlar ve aşağıdaki örnekte gösterildiği gibi kullanıcı adını, parolayı ve etki alanını ana bilgisayara geçirmek için bir nesne kullanır.  
  
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
  
 Uygulama kullanıcısının kimlik bilgilerini kullanarak Internet hizmetlerine bağlanması gereken uygulamalar, aşağıdaki örnekte gösterildiği gibi, kullanıcının varsayılan kimlik bilgileriyle bunu yapabilir.  
  
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
  
 Anlaşma kimlik doğrulama modülü uzak sunucunun NTLM veya Kerberos kimlik doğrulaması kullanıp kullanmadığını belirler ve uygun yanıtı gönderir.  
  
> [!NOTE]
> NTLM kimlik doğrulaması bir proxy sunucusu aracılığıyla çalışmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel ve Özet Kimlik Doğrulama](basic-and-digest-authentication.md)
- [İnternet Kimlik Doğrulaması](internet-authentication.md)
