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
# <a name="connection-grouping"></a>Bağlantı gruplandırma
Bağlantı gruplandırma tanımlanan bağlantı havuzu için tek bir uygulama içinde belirli isteklere ilişkilendirir. Bu kullanıcı adına bir arka uç sunucusuna bağlanır ve Kerberos gibi temsilci destekleyen kimlik doğrulama protokolünü kullanan Orta katman bir uygulama veya gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir Aşağıdaki örnek. Örneğin, bir kullanıcı, Can, kendi bordro bilgilerini görüntüler iç bir Web sitesini ziyaret varsayalım. Orta katman uygulama sunucusu Joe doğrulanmasından sonra kendi bordro bilgileri almak için arka uç sunucusuna bağlanmak için Can'ın kimlik bilgilerini kullanır. Ardından, Çiğdem sitesini ziyaret ve kendi bordro bilgilerini ister. Orta katman uygulama Can'ın kimlik bilgilerini kullanarak bir bağlantı zaten yaptığı arka uç sunucu Can'ın bilgilerle yanıt verir. Ancak, uygulamanın kullanıcı adından oluşturulmuş bir bağlantı grubu arka uç sunucusuna gönderilen her istek atarsa, ardından her kullanıcı için ayrı bağlantı havuzu aittir ve kimlik doğrulama bilgilerini başka bir kullanıcıyla yanlışlıkla paylaşamazsınız.  
  
 Bir istek belirli bağlantı gruba atamak için bir ad atayın <xref:System.Net.WebRequest.ConnectionGroupName%2A> özelliği, <xref:System.Net.WebRequest> isteği yapmadan önce.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantıları yönetme](../../../docs/framework/network-programming/managing-connections.md)  
 [Nasıl yapılır: Grup bağlantılar için kullanıcı bilgilerini atayın](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
