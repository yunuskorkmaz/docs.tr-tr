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
# <a name="connection-grouping"></a>Bağlantı Gruplandırma
Bağlantı gruplandırma, belirli istekleri tek bir uygulama daki tanımlı bir bağlantı havuzuna ilişkilendirer. Bu, bir kullanıcı adına bir arka uç sunucusuna bağlanan ve Kerberos gibi delegasyonu destekleyen bir kimlik doğrulama protokolü kullanan bir orta katman uygulaması veya aşağıdaki örnek. Örneğin, bir kullanıcının, Joe'nun bordro bilgilerini görüntüleyen dahili bir Web sitesini ziyaret ettiğini varsayalım. Joe'nun kimliğini doğruladıktan sonra, orta katman uygulama sunucusu bordro bilgilerini almak için arka uç sunucusuna bağlanmak için Joe'nun kimlik bilgilerini kullanır. Sonra, Susan siteyi ziyaret eder ve bordro bilgilerini ister. Orta katman uygulaması Joe'nun kimlik bilgilerini kullanarak zaten bir bağlantı kurmuş olduğundan, arka uç sunucusu Joe'nun bilgileriyle yanıt verir. Ancak, uygulama arka uç sunucusuna gönderilen her isteği kullanıcı adından oluşan bir bağlantı grubuna atarsa, her kullanıcı ayrı bir bağlantı havuzuna ait olur ve yanlışlıkla kimlik doğrulama bilgilerini başka bir kullanıcıyla paylaşamaz.  
  
 Belirli bir bağlantı grubuna istek atamak için, isteği <xref:System.Net.WebRequest.ConnectionGroupName%2A> yapmadan önce <xref:System.Net.WebRequest> mülkünüze bir ad atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları Yönetme](managing-connections.md)
- [Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama](how-to-assign-user-information-to-group-connections.md)
