---
title: Bağlantı gruplandırma
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5d7a13172c32d7ae47cbe290587ff7620e6060da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084753"
---
# <a name="connection-grouping"></a><span data-ttu-id="37739-102">Bağlantı gruplandırma</span><span class="sxs-lookup"><span data-stu-id="37739-102">Connection Grouping</span></span>
<span data-ttu-id="37739-103">Bağlantı gruplandırma için tanımlanan bağlantı havuzu tek bir uygulamada belirli isteklere ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="37739-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="37739-104">Bu bir kullanıcı adına arka uç sunucusuna bağlanır ve Kerberos gibi bir temsilci atamayı destekliyor bir kimlik doğrulama protokolü kullanan bir orta katman uygulama veya gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir Aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="37739-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="37739-105">Örneğin, ALi, bir kullanıcı kendi bordro bilgilerini görüntüleyen dahili bir Web sitesini ziyaret varsayalım.</span><span class="sxs-lookup"><span data-stu-id="37739-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="37739-106">Orta katman uygulama sunucusu ALi doğrulandıktan sonra bordro bilgilerini almak için arka uç sunucusuna bağlanmak için Can'ın kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="37739-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="37739-107">Ardından, Susan sitesini ziyaret ve kendi bordro bilgilerini ister.</span><span class="sxs-lookup"><span data-stu-id="37739-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="37739-108">Orta katman uygulama Can'ın kimlik bilgilerini kullanarak bir bağlantı zaten yaptığı arka uç sunucu Can'ın bilgilerle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="37739-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="37739-109">Ancak, uygulamanın arka uç sunucusuna bağlantı gruba kullanıcı adından oluşturulmuş gönderilen her istek atarsa, ardından her kullanıcı ayrı bağlantı havuzuna ait olan ve kimlik doğrulama bilgilerini başka bir kullanıcı yanlışlıkla paylaşamazsınız.</span><span class="sxs-lookup"><span data-stu-id="37739-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="37739-110">Bir istek belirli bağlantı gruba atamak için bir ad atamanız gerekir <xref:System.Net.WebRequest.ConnectionGroupName%2A> özelliği, <xref:System.Net.WebRequest> isteği yapmadan önce.</span><span class="sxs-lookup"><span data-stu-id="37739-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37739-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37739-111">See Also</span></span>  
 [<span data-ttu-id="37739-112">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="37739-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="37739-113">Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama</span><span class="sxs-lookup"><span data-stu-id="37739-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
