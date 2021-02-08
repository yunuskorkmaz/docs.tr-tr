---
description: 'Daha fazla bilgi edinin: bağlantı gruplandırması'
title: Bağlantı Gruplandırma
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 08e917b555da918ad4386a77938aeb57bc4e4ced
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791575"
---
# <a name="connection-grouping"></a><span data-ttu-id="71b70-103">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="71b70-103">Connection Grouping</span></span>

<span data-ttu-id="71b70-104">Bağlantı gruplandırması, tek bir uygulama içindeki belirli istekleri tanımlı bir bağlantı havuzu ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="71b70-104">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="71b70-105">Bu, bir kullanıcı adına arka uç sunucusuna bağlanan ve Kerberos gibi temsilciyi destekleyen bir kimlik doğrulama protokolü ya da aşağıdaki örnekte olduğu gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="71b70-105">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="71b70-106">Örneğin, bir kullanıcının, kendi bordro bilgilerini gösteren bir iç Web sitesini ziyaret ettiği bir kullanıcı olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="71b70-106">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="71b70-107">Joe kimlik doğrulamasından geçtikten sonra orta katmanlı uygulama sunucusu, ön uç sunucusuna bağlanmak için Joe kimlik bilgilerini kullanarak bordro bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="71b70-107">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="71b70-108">Daha sonra, Çiğdem siteyi ziyaret ettiğinde bordro bilgilerini ister.</span><span class="sxs-lookup"><span data-stu-id="71b70-108">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="71b70-109">Orta katman uygulama Joe kimlik bilgilerini kullanarak zaten bir bağlantı yaptığından, arka uç sunucusu Joe 'nun bilgileriyle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="71b70-109">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="71b70-110">Ancak, uygulama arka uç sunucusuna gönderilen her isteği Kullanıcı adından oluşturulmuş bir bağlantı grubuna atarsa, her kullanıcı ayrı bir bağlantı havuzuna aittir ve yanlışlıkla kimlik doğrulama bilgilerini başka bir kullanıcıyla paylaşamaz.</span><span class="sxs-lookup"><span data-stu-id="71b70-110">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="71b70-111">Belirli bir bağlantı grubuna istek atamak için, <xref:System.Net.WebRequest.ConnectionGroupName%2A> isteği yapmadan önce ' ın özelliğine bir ad atamanız gerekir <xref:System.Net.WebRequest> .</span><span class="sxs-lookup"><span data-stu-id="71b70-111">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b70-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71b70-112">See also</span></span>

- [<span data-ttu-id="71b70-113">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="71b70-113">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="71b70-114">Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama</span><span class="sxs-lookup"><span data-stu-id="71b70-114">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
