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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 66b20c299252ff1f218a8131758e2cf03640aac6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090103"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="4821d-102">Temel ve Özet kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="4821d-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="4821d-103"><xref:System.Net> Uygulama temel ve Özet kimlik doğrulaması uyan RFC2617 – HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması (www.w3.org World Wide Web Consortium'ın Web sitesinde kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="4821d-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the World Wide Web Consortium's Web site at www.w3.org).</span></span>  
  
 <span data-ttu-id="4821d-104">Temel kullanmak ve Özet kimlik doğrulaması için bir uygulama bir kullanıcı adı ve parola sağlamalıdır <xref:System.Net.WebRequest.Credentials%2A> özelliği <xref:System.Net.WebRequest> , aşağıdaki örnekte gösterildiği gibi Internet'ten veri isteği için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="4821d-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="4821d-105">Temel ve Özet kimlik doğrulaması ile gönderilen veriler şifrelenmez, bu şekilde verileri bir saldırgan tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="4821d-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="4821d-106">Ayrıca, temel kimlik doğrulaması kimlik bilgilerini (kullanıcı adı ve parola) açık bir şekilde gönderilir ve kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="4821d-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4821d-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4821d-107">See Also</span></span>  
 [<span data-ttu-id="4821d-108">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4821d-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [<span data-ttu-id="4821d-109">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4821d-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
