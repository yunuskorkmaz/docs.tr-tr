---
title: "Bağlantı gruplandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b947051d809d5e8f5be3410b269c872bfc108ec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="connection-grouping"></a><span data-ttu-id="d2d79-102">Bağlantı gruplandırma</span><span class="sxs-lookup"><span data-stu-id="d2d79-102">Connection Grouping</span></span>
<span data-ttu-id="d2d79-103">Bağlantı gruplandırma tanımlanan bağlantı havuzu için tek bir uygulama içinde belirli isteklere ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d2d79-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="d2d79-104">Bu kullanıcı adına bir arka uç sunucusuna bağlanır ve Kerberos gibi temsilci destekleyen kimlik doğrulama protokolünü kullanan Orta katman bir uygulama veya gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir Aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="d2d79-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="d2d79-105">Örneğin, bir kullanıcı, Can, kendi bordro bilgilerini görüntüler iç bir Web sitesini ziyaret varsayalım.</span><span class="sxs-lookup"><span data-stu-id="d2d79-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="d2d79-106">Orta katman uygulama sunucusu Joe doğrulanmasından sonra kendi bordro bilgileri almak için arka uç sunucusuna bağlanmak için Can'ın kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d2d79-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="d2d79-107">Ardından, Çiğdem sitesini ziyaret ve kendi bordro bilgilerini ister.</span><span class="sxs-lookup"><span data-stu-id="d2d79-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="d2d79-108">Orta katman uygulama Can'ın kimlik bilgilerini kullanarak bir bağlantı zaten yaptığı arka uç sunucu Can'ın bilgilerle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d2d79-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="d2d79-109">Ancak, uygulamanın kullanıcı adından oluşturulmuş bir bağlantı grubu arka uç sunucusuna gönderilen her istek atarsa, ardından her kullanıcı için ayrı bağlantı havuzu aittir ve kimlik doğrulama bilgilerini başka bir kullanıcıyla yanlışlıkla paylaşamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d2d79-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="d2d79-110">Bir istek belirli bağlantı gruba atamak için bir ad atayın <xref:System.Net.WebRequest.ConnectionGroupName%2A> özelliği, <xref:System.Net.WebRequest> isteği yapmadan önce.</span><span class="sxs-lookup"><span data-stu-id="d2d79-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d79-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2d79-111">See Also</span></span>  
 [<span data-ttu-id="d2d79-112">Bağlantıları yönetme</span><span class="sxs-lookup"><span data-stu-id="d2d79-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="d2d79-113">Nasıl yapılır: Grup bağlantılar için kullanıcı bilgilerini atayın</span><span class="sxs-lookup"><span data-stu-id="d2d79-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
