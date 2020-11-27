---
title: IPv6 Otomatik Yapılandırma
description: IPv6 'nın bir IPv6 ağını birleştiren ve insan müdahalesi olmadan yapılandırıldığı düğüm Tak ve Kullan nasıl desteklediğini öğrenin.
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: db6156433e21411ff1e88634a359bbde7528fd91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258380"
---
# <a name="ipv6-auto-configuration"></a>IPv6 Otomatik Yapılandırma

IPv6 için önemli bir amaç, düğüm Tak ve Kullan destekolmaktır. Diğer bir deyişle, bir IPv6 ağına bir düğüm bağlamak ve herhangi bir insan müdahalesi olmadan otomatik olarak yapılandırılmasını sağlamak mümkün olmalıdır.  
  
## <a name="type-of-auto-configuration"></a>Otomatik yapılandırma türü  

 IPv6, aşağıdaki otomatik yapılandırma türlerini destekler:  
  
- **Durum bilgisi olan otomatik yapılandırma**. Bu tür bir yapılandırma, düğümlerin yüklenmesi ve yönetilmesi için bir IPv6 (DHCPv6) sunucusu için dinamik ana bilgisayar Yapılandırma Protokolü gerektirdiğinden belirli bir insan müdahalesi düzeyi gerektirir. DHCPv6 sunucusu, yapılandırma bilgilerini sağladığı düğümlerin bir listesini tutar. Ayrıca, sunucunun her bir adresin ne kadar süreyle kullanımda olduğunu ve yeniden atamaya uygun olabileceğini bilmesi için durum bilgilerini korur.  
  
- **Durum bilgisiz otomatik yapılandırma**. Bu tür bir yapılandırma, küçük kuruluşlar ve bireyler için uygundur. Bu durumda, her ana bilgisayar, alınan yönlendirici tanıtımlarının içeriğiyle ilgili adreslerini belirler. Adresin ağ KIMLIĞI bölümünü tanımlamak için IEEE EUı-64 standardını kullanarak, bağlantı üzerinde ana bilgisayar adresinin benzersizlik düzeyini varsaymak mantıklı değildir.  
  
 Adresin nasıl belirlendiğine bakılmaksızın, düğüm potansiyel adresinin yerel bağlantı için benzersiz olduğunu doğrulamalıdır. Bu, olası adrese bir komşu isteği iletisi gönderilerek yapılır. Düğüm herhangi bir yanıt alırsa, adresin zaten kullanımda olduğunu ve başka bir adresi belirlemesi gerektiğini bilir.  
  
## <a name="ipv6-mobility"></a>IPv6 Mobility  

 Mobil cihazların kullanılması yeni bir gereksinim sunmuştur: bir cihazın IPv6 Internet 'teki konumları rastgele değiştirebilmeleri ve mevcut bağlantıları sürdürmeye devam edilmesi gerekir. Bu işlevi sağlamak için bir mobil düğüme her zaman ulaşılabileceği bir giriş adresi atanır. Mobil düğüm evde olduğunda, giriş bağlantısına bağlanır ve ev adresini kullanır. Mobil düğüm evden uzakta olduğunda, genellikle yönlendirici olan bir ana aracı, iletişim kurduğu mobil düğüm ve düğümler arasında ileti geçirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
