---
title: Temel ve Özet Kimlik Doğrulaması
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
ms.openlocfilehash: 4f70d2aef3bb064a3df9db9c87671040776332a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866905"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="d4034-102">Temel ve Özet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d4034-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="d4034-103"><xref:System.Net> Uygulama temel ve Özet kimlik doğrulaması RFC2617 – HTTP kimlik doğrulaması ile uyumludur: Temel ve Özet kimlik doğrulaması (kullanılabilir [World Wide Web Consortium'ın](https://www.w3.org) Web sitesi).</span><span class="sxs-lookup"><span data-stu-id="d4034-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="d4034-104">Temel kullanmak ve Özet kimlik doğrulaması için bir uygulama bir kullanıcı adı ve parola sağlamalıdır <xref:System.Net.WebRequest.Credentials%2A> özelliği <xref:System.Net.WebRequest> , aşağıdaki örnekte gösterildiği gibi Internet'ten veri isteği için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="d4034-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="d4034-105">Temel ve Özet kimlik doğrulaması ile gönderilen veriler şifrelenmez, bu şekilde verileri bir saldırgan tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="d4034-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="d4034-106">Ayrıca, temel kimlik doğrulaması kimlik bilgilerini (kullanıcı adı ve parola) açık bir şekilde gönderilir ve kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4034-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4034-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4034-107">See also</span></span>

- [<span data-ttu-id="d4034-108">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d4034-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="d4034-109">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d4034-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
