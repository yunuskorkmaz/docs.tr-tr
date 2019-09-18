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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048907"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="444f9-102">Temel ve Özet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="444f9-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="444f9-103">Temel ve Özet kimlik doğrulamasının uygulanmasıRFC2617–httpkimlikdoğrulamasıileuyumludur:<xref:System.Net> Temel ve Özet kimlik doğrulaması ( [World Wide Web Konsorsiyumu](https://www.w3.org) Web sitesinde kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="444f9-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="444f9-104">Temel ve Özet kimlik doğrulamasını kullanmak için bir uygulamanın, aşağıdaki örnekte gösterildiği gibi, Internet 'ten veri <xref:System.Net.WebRequest.Credentials%2A> istemek için kullandığı <xref:System.Net.WebRequest> nesnenin özelliğinde bir Kullanıcı adı ve parola sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="444f9-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="444f9-105">Temel ve Özet kimlik doğrulamasıyla gönderilen veriler şifrelenmemiştir, bu nedenle veriler bir saldırgan tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="444f9-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="444f9-106">Ayrıca, temel kimlik doğrulama kimlik bilgileri (Kullanıcı adı ve parola) açık olarak gönderilir ve yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="444f9-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444f9-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="444f9-107">See also</span></span>

- [<span data-ttu-id="444f9-108">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="444f9-108">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="444f9-109">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="444f9-109">Internet Authentication</span></span>](internet-authentication.md)
