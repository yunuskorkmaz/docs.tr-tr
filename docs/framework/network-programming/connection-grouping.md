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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184579"
---
# <a name="connection-grouping"></a>Bağlantı Gruplandırma
Bağlantı gruplandırma için tanımlanan bağlantı havuzu tek bir uygulamada belirli isteklere ilişkilendirir. Bu bir kullanıcı adına arka uç sunucusuna bağlanır ve Kerberos gibi bir temsilci atamayı destekliyor bir kimlik doğrulama protokolü kullanan bir orta katman uygulama veya gibi kendi kimlik bilgilerini sağlayan bir orta katman uygulama tarafından gerekli olabilir Aşağıdaki örnek. Örneğin, ALi, bir kullanıcı kendi bordro bilgilerini görüntüleyen dahili bir Web sitesini ziyaret varsayalım. Orta katman uygulama sunucusu ALi doğrulandıktan sonra bordro bilgilerini almak için arka uç sunucusuna bağlanmak için Can'ın kimlik bilgilerini kullanır. Ardından, Susan sitesini ziyaret ve kendi bordro bilgilerini ister. Orta katman uygulama Can'ın kimlik bilgilerini kullanarak bir bağlantı zaten yaptığı arka uç sunucu Can'ın bilgilerle yanıt verir. Ancak, uygulamanın arka uç sunucusuna bağlantı gruba kullanıcı adından oluşturulmuş gönderilen her istek atarsa, ardından her kullanıcı ayrı bağlantı havuzuna ait olan ve kimlik doğrulama bilgilerini başka bir kullanıcı yanlışlıkla paylaşamazsınız.  
  
 Bir istek belirli bağlantı gruba atamak için bir ad atamanız gerekir <xref:System.Net.WebRequest.ConnectionGroupName%2A> özelliği, <xref:System.Net.WebRequest> isteği yapmadan önce.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları Yönetme](../../../docs/framework/network-programming/managing-connections.md)
- [Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
