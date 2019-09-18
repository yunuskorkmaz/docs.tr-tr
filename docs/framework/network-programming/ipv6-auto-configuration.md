---
title: IPv6 Otomatik Yapılandırma
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 95d9dce36c70b8f6c6b9f963c0842305a111d436
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047818"
---
# <a name="ipv6-auto-configuration"></a>IPv6 Otomatik Yapılandırma
IPv6 için önemli bir amaç, düğüm Tak ve Kullan destekolmaktır. Diğer bir deyişle, bir IPv6 ağına bir düğüm bağlamak ve herhangi bir insan müdahalesi olmadan otomatik olarak yapılandırılmasını sağlamak mümkün olmalıdır.  
  
## <a name="type-of-auto-configuration"></a>Otomatik yapılandırma türü  
 IPv6, aşağıdaki otomatik yapılandırma türlerini destekler:  
  
- **Durum bilgisi olan otomatik yapılandırma**. Bu tür bir yapılandırma, düğümlerin yüklenmesi ve yönetilmesi için bir IPv6 (DHCPv6) sunucusu için dinamik ana bilgisayar Yapılandırma Protokolü gerektirdiğinden belirli bir insan müdahalesi düzeyi gerektirir. DHCPv6 sunucusu, yapılandırma bilgilerini sağladığı düğümlerin bir listesini tutar. Ayrıca, sunucunun her bir adresin ne kadar süreyle kullanımda olduğunu ve yeniden atamaya uygun olabileceğini bilmesi için durum bilgilerini korur.  
  
- **Durum bilgisiz otomatik yapılandırma**. Bu tür bir yapılandırma, küçük kuruluşlar ve bireyler için uygundur. Bu durumda, her ana bilgisayar, alınan yönlendirici tanıtımlarının içeriğiyle ilgili adreslerini belirler. Adresin ağ KIMLIĞI bölümünü tanımlamak için IEEE EUı-64 standardını kullanarak, bağlantı üzerinde ana bilgisayar adresinin benzersizlik düzeyini varsaymak mantıklı değildir.  
  
 Adresin nasıl belirlendiğine bakılmaksızın, düğüm potansiyel adresinin yerel bağlantı için benzersiz olduğunu doğrulamalıdır. Bu, olası adrese bir komşu isteği iletisi gönderilerek yapılır. Düğüm herhangi bir yanıt alırsa, adresin zaten kullanımda olduğunu ve başka bir adresi belirlemesi gerektiğini bilir.  
  
## <a name="ipv6-mobility"></a>IPv6 Mobility  
 Mobil cihazların kullanımı yeni bir gereksinim getirmiştir: Bir cihazın IPv6 Internet üzerindeki konumları rastgele değiştirmesi ve yine de mevcut bağlantıları sürdürbilmeleri gerekir. Bu işlevi sağlamak için bir mobil düğüme her zaman ulaşılabileceği bir giriş adresi atanır. Mobil düğüm evde olduğunda, giriş bağlantısına bağlanır ve ev adresini kullanır. Mobil düğüm evden uzakta olduğunda, genellikle yönlendirici olan bir ana aracı, iletişim kurduğu mobil düğüm ve düğümler arasında ileti geçirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
