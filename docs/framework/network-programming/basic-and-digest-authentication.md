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
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="1d57c-102">Temel ve Özet kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="1d57c-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="1d57c-103"><xref:System.Net> Uygulama temel ve Özet kimlik doğrulaması RFC2617 – HTTP kimlik doğrulaması ile uyumludur: Temel ve Özet kimlik doğrulaması (kullanılabilir [World Wide Web Consortium'ın](https://www.w3.org) Web sitesi).</span><span class="sxs-lookup"><span data-stu-id="1d57c-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="1d57c-104">Temel kullanmak ve Özet kimlik doğrulaması için bir uygulama bir kullanıcı adı ve parola sağlamalıdır <xref:System.Net.WebRequest.Credentials%2A> özelliği <xref:System.Net.WebRequest> , aşağıdaki örnekte gösterildiği gibi Internet'ten veri isteği için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="1d57c-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="1d57c-105">Temel ve Özet kimlik doğrulaması ile gönderilen veriler şifrelenmez, bu şekilde verileri bir saldırgan tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="1d57c-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="1d57c-106">Ayrıca, temel kimlik doğrulaması kimlik bilgilerini (kullanıcı adı ve parola) açık bir şekilde gönderilir ve kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="1d57c-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d57c-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d57c-107">See also</span></span>
- [<span data-ttu-id="1d57c-108">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="1d57c-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="1d57c-109">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="1d57c-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
