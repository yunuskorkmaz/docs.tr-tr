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
# <a name="connection-grouping"></a>Bağlantı Gruplandırma

Bağlantı gruplandırması, tek bir uygulama içindeki belirli istekleri tanımlı bir bağlantı havuzu ile ilişkilendirir. Bu, bir kullanıcı adına arka uç sunucusuna bağlanan ve Kerberos gibi temsilciyi destekleyen bir kimlik doğrulama protokolü ya da aşağıdaki örnekte olduğu gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir. Örneğin, bir kullanıcının, kendi bordro bilgilerini gösteren bir iç Web sitesini ziyaret ettiği bir kullanıcı olduğunu varsayalım. Joe kimlik doğrulamasından geçtikten sonra orta katmanlı uygulama sunucusu, ön uç sunucusuna bağlanmak için Joe kimlik bilgilerini kullanarak bordro bilgilerini alır. Daha sonra, Çiğdem siteyi ziyaret ettiğinde bordro bilgilerini ister. Orta katman uygulama Joe kimlik bilgilerini kullanarak zaten bir bağlantı yaptığından, arka uç sunucusu Joe 'nun bilgileriyle yanıt verir. Ancak, uygulama arka uç sunucusuna gönderilen her isteği Kullanıcı adından oluşturulmuş bir bağlantı grubuna atarsa, her kullanıcı ayrı bir bağlantı havuzuna aittir ve yanlışlıkla kimlik doğrulama bilgilerini başka bir kullanıcıyla paylaşamaz.  
  
 Belirli bir bağlantı grubuna istek atamak için, <xref:System.Net.WebRequest.ConnectionGroupName%2A> isteği yapmadan önce ' ın özelliğine bir ad atamanız gerekir <xref:System.Net.WebRequest> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları Yönetme](managing-connections.md)
- [Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama](how-to-assign-user-information-to-group-connections.md)
