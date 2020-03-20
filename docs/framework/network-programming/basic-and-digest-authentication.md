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
ms.openlocfilehash: 9a1ad701e1e8f4ee9966ebd56922c29e2bae7a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048907"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="1594e-102">Temel ve Özet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="1594e-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="1594e-103">Temel <xref:System.Net> ve özet kimlik doğrulamasının uygulanması RFC2617 – HTTP Kimlik Doğrulama: Temel ve Özet Kimlik Doğrulama [(World Wide Web Konsorsiyumu'nun](https://www.w3.org) web sitesinde mevcuttur) ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="1594e-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="1594e-104">Temel ve özet kimlik doğrulamasını kullanmak için, uygulamanın <xref:System.Net.WebRequest.Credentials%2A> aşağıdaki örnekte gösterildiği gibi, Internet'ten veri istemek için kullandığı <xref:System.Net.WebRequest> nesnenin özelliğinde bir kullanıcı adı ve parola sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1594e-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="1594e-105">Temel ve Özet Kimlik Doğrulama ile gönderilen veriler şifrelenmez, bu nedenle veriler bir rakip tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="1594e-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="1594e-106">Ayrıca, Temel Kimlik Doğrulama kimlik bilgileri (kullanıcı adı ve parola) açık olarak gönderilir ve ele geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1594e-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1594e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1594e-107">See also</span></span>

- [<span data-ttu-id="1594e-108">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="1594e-108">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="1594e-109">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="1594e-109">Internet Authentication</span></span>](internet-authentication.md)
