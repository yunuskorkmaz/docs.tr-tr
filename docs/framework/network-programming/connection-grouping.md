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
ms.openlocfilehash: 00ccc11919f0ccd4f9361bfd8f265dea1ad2390d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184579"
---
# <a name="connection-grouping"></a><span data-ttu-id="bcc46-102">Bağlantı Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="bcc46-102">Connection Grouping</span></span>
<span data-ttu-id="bcc46-103">Bağlantı gruplandırma için tanımlanan bağlantı havuzu tek bir uygulamada belirli isteklere ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="bcc46-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="bcc46-104">Bu bir kullanıcı adına arka uç sunucusuna bağlanır ve Kerberos gibi bir temsilci atamayı destekliyor bir kimlik doğrulama protokolü kullanan bir orta katman uygulama veya gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir Aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="bcc46-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="bcc46-105">Örneğin, ALi, bir kullanıcı kendi bordro bilgilerini görüntüleyen dahili bir Web sitesini ziyaret varsayalım.</span><span class="sxs-lookup"><span data-stu-id="bcc46-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="bcc46-106">Orta katman uygulama sunucusu ALi doğrulandıktan sonra bordro bilgilerini almak için arka uç sunucusuna bağlanmak için Can'ın kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bcc46-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="bcc46-107">Ardından, Susan sitesini ziyaret ve kendi bordro bilgilerini ister.</span><span class="sxs-lookup"><span data-stu-id="bcc46-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="bcc46-108">Orta katman uygulama Can'ın kimlik bilgilerini kullanarak bir bağlantı zaten yaptığı arka uç sunucu Can'ın bilgilerle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="bcc46-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="bcc46-109">Ancak, uygulamanın arka uç sunucusuna bağlantı gruba kullanıcı adından oluşturulmuş gönderilen her istek atarsa, ardından her kullanıcı ayrı bağlantı havuzuna ait olan ve kimlik doğrulama bilgilerini başka bir kullanıcı yanlışlıkla paylaşamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bcc46-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="bcc46-110">Bir istek belirli bağlantı gruba atamak için bir ad atamanız gerekir <xref:System.Net.WebRequest.ConnectionGroupName%2A> özelliği, <xref:System.Net.WebRequest> isteği yapmadan önce.</span><span class="sxs-lookup"><span data-stu-id="bcc46-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc46-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcc46-111">See also</span></span>

- [<span data-ttu-id="bcc46-112">Bağlantıları Yönetme</span><span class="sxs-lookup"><span data-stu-id="bcc46-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)
- [<span data-ttu-id="bcc46-113">Nasıl yapılır: Bağlantıları gruplandırmak için kullanıcı bilgileri atama</span><span class="sxs-lookup"><span data-stu-id="bcc46-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
