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
ms.openlocfilehash: 007366764a7b8e1208e22ef5895e6a9093b090e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048639"
---
# <a name="connection-grouping"></a><span data-ttu-id="846ec-102">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="846ec-102">Connection Grouping</span></span>
<span data-ttu-id="846ec-103">Bağlantı gruplandırma, belirli istekleri tek bir uygulama daki tanımlı bir bağlantı havuzuna ilişkilendirer.</span><span class="sxs-lookup"><span data-stu-id="846ec-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="846ec-104">Bu, bir kullanıcı adına bir arka uç sunucusuna bağlanan ve Kerberos gibi delegasyonu destekleyen bir kimlik doğrulama protokolü kullanan bir orta katman uygulaması veya aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="846ec-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="846ec-105">Örneğin, bir kullanıcının, Joe'nun bordro bilgilerini görüntüleyen dahili bir Web sitesini ziyaret ettiğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="846ec-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="846ec-106">Joe'nun kimliğini doğruladıktan sonra, orta katman uygulama sunucusu bordro bilgilerini almak için arka uç sunucusuna bağlanmak için Joe'nun kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="846ec-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="846ec-107">Sonra, Susan siteyi ziyaret eder ve bordro bilgilerini ister.</span><span class="sxs-lookup"><span data-stu-id="846ec-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="846ec-108">Orta katman uygulaması Joe'nun kimlik bilgilerini kullanarak zaten bir bağlantı kurmuş olduğundan, arka uç sunucusu Joe'nun bilgileriyle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="846ec-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="846ec-109">Ancak, uygulama arka uç sunucusuna gönderilen her isteği kullanıcı adından oluşan bir bağlantı grubuna atarsa, her kullanıcı ayrı bir bağlantı havuzuna ait olur ve yanlışlıkla kimlik doğrulama bilgilerini başka bir kullanıcıyla paylaşamaz.</span><span class="sxs-lookup"><span data-stu-id="846ec-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="846ec-110">Belirli bir bağlantı grubuna istek atamak için, isteği <xref:System.Net.WebRequest.ConnectionGroupName%2A> yapmadan önce <xref:System.Net.WebRequest> mülkünüze bir ad atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="846ec-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846ec-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="846ec-111">See also</span></span>

- [<span data-ttu-id="846ec-112">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="846ec-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="846ec-113">Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama</span><span class="sxs-lookup"><span data-stu-id="846ec-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
