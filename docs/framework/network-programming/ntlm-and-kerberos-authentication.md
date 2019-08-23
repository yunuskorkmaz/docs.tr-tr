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
ms.openlocfilehash: b05cd88fcb492ab27e1d311045b72208167508f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963931"
---
# <a name="ntlm-and-kerberos-authentication"></a>NTLM ve Kerberos Kimlik Doğrulaması
Varsayılan NTLM kimlik doğrulaması ve Kerberos kimlik doğrulaması, sunucuyla kimlik doğrulamayı denemek için çağıran uygulamayla ilişkili Microsoft Windows NT Kullanıcı kimlik bilgilerini kullanır. Varsayılan olmayan NTLM kimlik doğrulaması kullanılırken, uygulama kimlik doğrulama türünü NTLM olarak ayarlar ve aşağıdaki örnekte gösterildiği gibi <xref:System.Net.NetworkCredential> Kullanıcı adını, parolayı ve etki alanını konağa geçirmek için bir nesne kullanır.  
  
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
  
 Uygulama kullanıcısının kimlik bilgilerini kullanarak Internet hizmetlerine bağlanması gereken uygulamalar, aşağıdaki örnekte gösterildiği gibi kullanıcının varsayılan kimlik bilgileriyle bunu yapabilir.  
  
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
  
 Negotiate kimlik doğrulama modülü, uzak sunucunun NTLM veya Kerberos kimlik doğrulaması kullanıp kullanmadığını belirler ve uygun yanıtı gönderir.  
  
> [!NOTE]
> NTLM kimlik doğrulaması bir ara sunucu üzerinden çalışmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel ve Özet Kimlik Doğrulama](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [İnternet Kimlik Doğrulaması](../../../docs/framework/network-programming/internet-authentication.md)
