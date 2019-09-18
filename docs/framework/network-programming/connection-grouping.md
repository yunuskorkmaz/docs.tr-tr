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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048639"
---
# <a name="connection-grouping"></a>Bağlantı Gruplandırma
Bağlantı gruplandırması, tek bir uygulama içindeki belirli istekleri tanımlı bir bağlantı havuzu ile ilişkilendirir. Bu, bir kullanıcı adına arka uç sunucusuna bağlanan ve Kerberos gibi temsilciyi destekleyen bir kimlik doğrulama protokolü (örneğin, kendi kimlik bilgilerini sağlayan bir orta katman uygulaması tarafından), Aşağıda örnek. Örneğin, bir kullanıcının, kendi bordro bilgilerini gösteren bir iç Web sitesini ziyaret ettiği bir kullanıcı olduğunu varsayalım. Joe kimlik doğrulamasından geçtikten sonra orta katmanlı uygulama sunucusu, ön uç sunucusuna bağlanmak için Joe kimlik bilgilerini kullanarak bordro bilgilerini alır. Daha sonra, Çiğdem siteyi ziyaret ettiğinde bordro bilgilerini ister. Orta katman uygulama Joe kimlik bilgilerini kullanarak zaten bir bağlantı yaptığından, arka uç sunucusu Joe 'nun bilgileriyle yanıt verir. Ancak, uygulama arka uç sunucusuna gönderilen her isteği Kullanıcı adından oluşturulmuş bir bağlantı grubuna atarsa, her kullanıcı ayrı bir bağlantı havuzuna aittir ve yanlışlıkla kimlik doğrulama bilgilerini başka bir kullanıcıyla paylaşamaz.  
  
 Belirli bir bağlantı grubuna istek atamak için, isteği yapmadan <xref:System.Net.WebRequest.ConnectionGroupName%2A> <xref:System.Net.WebRequest> önce ' ın özelliğine bir ad atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları Yönetme](managing-connections.md)
- [Nasıl yapılır: Grup bağlantılarına Kullanıcı bilgilerini atama](how-to-assign-user-information-to-group-connections.md)
