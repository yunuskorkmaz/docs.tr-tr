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
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="ead95-102">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ead95-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="ead95-103">Varsayılan NTLM kimlik doğrulaması ve Kerberos kimlik doğrulaması, sunucuyla kimlik doğrulamayı denemek için arama uygulamasıyla ilişkili Microsoft Windows NT kullanıcı kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ead95-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="ead95-104">Varsayılan olmayan NTLM kimlik doğrulaması kullanırken, uygulama kimlik doğrulama türünü <xref:System.Net.NetworkCredential> NTLM olarak ayarlar ve aşağıdaki örnekte gösterildiği gibi kullanıcı adını, parolayı ve etki alanını ana bilgisayara geçirmek için bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="ead95-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ead95-105">Uygulama kullanıcısının kimlik bilgilerini kullanarak Internet hizmetlerine bağlanması gereken uygulamalar, aşağıdaki örnekte gösterildiği gibi, kullanıcının varsayılan kimlik bilgileriyle bunu yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ead95-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ead95-106">Anlaşma kimlik doğrulama modülü uzak sunucunun NTLM veya Kerberos kimlik doğrulaması kullanıp kullanmadığını belirler ve uygun yanıtı gönderir.</span><span class="sxs-lookup"><span data-stu-id="ead95-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ead95-107">NTLM kimlik doğrulaması bir proxy sunucusu aracılığıyla çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="ead95-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead95-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ead95-108">See also</span></span>

- [<span data-ttu-id="ead95-109">Temel ve Özet Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="ead95-109">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="ead95-110">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ead95-110">Internet Authentication</span></span>](internet-authentication.md)
