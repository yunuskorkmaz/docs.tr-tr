---
title: Bağlantı Gruplandırma
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 8bd4412a4c13dd490fce3118f59b5bb1f0d3ea85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250573"
---
# <a name="connection-grouping"></a><span data-ttu-id="44126-102">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="44126-102">Connection Grouping</span></span>

<span data-ttu-id="44126-103">Bağlantı gruplandırması, tek bir uygulama içindeki belirli istekleri tanımlı bir bağlantı havuzu ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="44126-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="44126-104">Bu, bir kullanıcı adına arka uç sunucusuna bağlanan ve Kerberos gibi temsilciyi destekleyen bir kimlik doğrulama protokolü ya da aşağıdaki örnekte olduğu gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="44126-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="44126-105">Örneğin, bir kullanıcının, kendi bordro bilgilerini gösteren bir iç Web sitesini ziyaret ettiği bir kullanıcı olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="44126-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="44126-106">Joe kimlik doğrulamasından geçtikten sonra orta katmanlı uygulama sunucusu, ön uç sunucusuna bağlanmak için Joe kimlik bilgilerini kullanarak bordro bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="44126-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="44126-107">Daha sonra, Çiğdem siteyi ziyaret ettiğinde bordro bilgilerini ister.</span><span class="sxs-lookup"><span data-stu-id="44126-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="44126-108">Orta katman uygulama Joe kimlik bilgilerini kullanarak zaten bir bağlantı yaptığından, arka uç sunucusu Joe 'nun bilgileriyle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="44126-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="44126-109">Ancak, uygulama arka uç sunucusuna gönderilen her isteği Kullanıcı adından oluşturulmuş bir bağlantı grubuna atarsa, her kullanıcı ayrı bir bağlantı havuzuna aittir ve yanlışlıkla kimlik doğrulama bilgilerini başka bir kullanıcıyla paylaşamaz.</span><span class="sxs-lookup"><span data-stu-id="44126-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="44126-110">Belirli bir bağlantı grubuna istek atamak için, <xref:System.Net.WebRequest.ConnectionGroupName%2A> isteği yapmadan önce ' ın özelliğine bir ad atamanız gerekir <xref:System.Net.WebRequest> .</span><span class="sxs-lookup"><span data-stu-id="44126-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44126-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44126-111">See also</span></span>

- [<span data-ttu-id="44126-112">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="44126-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="44126-113">Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama</span><span class="sxs-lookup"><span data-stu-id="44126-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
