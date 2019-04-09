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
ms.openlocfilehash: 2efb2d25e1b7566e3405a699be1795b37d549091
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183371"
---
# <a name="ntlm-and-kerberos-authentication"></a>NTLM ve Kerberos Kimlik Doğrulaması
Varsayılan NTLM kimlik doğrulaması ve Kerberos kimlik doğrulama sunucusu ile kimlik doğrulamasını kullanmayı denemek çağıran uygulama ile ilişkili Microsoft Windows NT kullanıcı kimlik bilgilerini kullanın. Varsayılan olmayan NTLM kimlik doğrulaması kullanırken, uygulama kimlik doğrulama türü NTLM olarak ayarlar ve kullandığı bir <xref:System.Net.NetworkCredential> kullanıcı adı, parola ve etki alanı aşağıdaki örnekte gösterildiği gibi ana bilgisayara geçirmek için nesne.  
  
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
  
 Uygulama kullanıcısı kimlik bilgilerini kullanarak Internet hizmetlerine bağlanmak için gereken uygulamalar aşağıdaki örnekte gösterildiği gibi kullanıcının varsayılan kimlik bilgileri ile bunu yapabilirsiniz.  
  
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
  
 Anlaşma kimlik doğrulama modülü, uzak sunucu NTLM veya Kerberos kimlik doğrulaması kullanarak ve uygun yanıtı gönderen olup olmadığını belirler.  
  
> [!NOTE]
>  NTLM kimlik doğrulaması, bir proxy sunucu üzerinden çalışmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel ve Özet Kimlik Doğrulaması](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [İnternet Kimlik Doğrulaması](../../../docs/framework/network-programming/internet-authentication.md)
