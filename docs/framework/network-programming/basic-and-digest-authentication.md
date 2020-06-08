---
title: Temel ve Özet Kimlik Doğrulaması
description: Bir uygulamanın, veri istemek için kullandığı WebRequest nesnesinde bir Kullanıcı adı ve parola sağladığı temel ve Özet kimlik doğrulamasını kullanmayı öğrenin.
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
ms.openlocfilehash: 7772430b508b52a63d716550b69018385418c132
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502710"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="dfa01-103">Temel ve Özet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="dfa01-103">Basic and Digest Authentication</span></span>
<span data-ttu-id="dfa01-104"><xref:System.Net>Temel ve Özet kimlik doğrulamasının UYGULANMASı RFC2617 – http kimlik doğrulaması: temel ve Özet kimlik doğrulaması ( [World Wide Web Konsorsiyumu 'ın](https://www.w3.org) Web sitesinde bulunur) ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="dfa01-104">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="dfa01-105">Temel ve Özet kimlik doğrulamasını kullanmak için bir uygulamanın, <xref:System.Net.WebRequest.Credentials%2A> <xref:System.Net.WebRequest> Aşağıdaki örnekte gösterildiği gibi, Internet 'ten veri istemek için kullandığı nesnenin özelliğinde bir Kullanıcı adı ve parola sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfa01-105">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="dfa01-106">Temel ve Özet kimlik doğrulamasıyla gönderilen veriler şifrelenmemiştir, bu nedenle veriler bir saldırgan tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="dfa01-106">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="dfa01-107">Ayrıca, temel kimlik doğrulama kimlik bilgileri (Kullanıcı adı ve parola) açık olarak gönderilir ve yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="dfa01-107">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa01-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfa01-108">See also</span></span>

- [<span data-ttu-id="dfa01-109">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="dfa01-109">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="dfa01-110">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="dfa01-110">Internet Authentication</span></span>](internet-authentication.md)
