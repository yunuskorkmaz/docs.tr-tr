---
title: NTLM ve Kerberos kimlik doğrulaması
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e7638b9558363b77b03208d86d98330b922b414c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195488"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="f6b77-102">NTLM ve Kerberos kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f6b77-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="f6b77-103">Varsayılan NTLM kimlik doğrulaması ve Kerberos kimlik doğrulama sunucusu ile kimlik doğrulamasını kullanmayı denemek çağıran uygulama ile ilişkili Microsoft Windows NT kullanıcı kimlik bilgilerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6b77-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="f6b77-104">Varsayılan olmayan NTLM kimlik doğrulaması kullanırken, uygulama kimlik doğrulama türü NTLM olarak ayarlar ve kullandığı bir <xref:System.Net.NetworkCredential> kullanıcı adı, parola ve etki alanı aşağıdaki örnekte gösterildiği gibi ana bilgisayara geçirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="f6b77-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="f6b77-105">Uygulama kullanıcısı kimlik bilgilerini kullanarak Internet hizmetlerine bağlanmak için gereken uygulamalar aşağıdaki örnekte gösterildiği gibi kullanıcının varsayılan kimlik bilgileri ile bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6b77-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="f6b77-106">Anlaşma kimlik doğrulama modülü, uzak sunucu NTLM veya Kerberos kimlik doğrulaması kullanarak ve uygun yanıtı gönderen olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f6b77-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6b77-107">NTLM kimlik doğrulaması, bir proxy sunucu üzerinden çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f6b77-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b77-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6b77-108">See Also</span></span>  
 [<span data-ttu-id="f6b77-109">Temel ve Özet Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="f6b77-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [<span data-ttu-id="f6b77-110">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f6b77-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
