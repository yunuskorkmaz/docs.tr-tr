---
title: IPv6 Otomatik Yapılandırma
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 95d9dce36c70b8f6c6b9f963c0842305a111d436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047818"
---
# <a name="ipv6-auto-configuration"></a>IPv6 Otomatik Yapılandırma
IPv6 için önemli bir hedef düğüm Tak ve Çalıştır'ı desteklemektir. Diğer bir zamanda, bir düğümbir IPv6 ağına takmak ve herhangi bir insan müdahalesi olmadan otomatik olarak yapılandırılması mümkün olmalıdır.  
  
## <a name="type-of-auto-configuration"></a>Otomatik Yapılandırma Türü  
 IPv6 aşağıdaki otomatik yapılandırma türlerini destekler:  
  
- **Stateful otomatik yapılandırma.** Düğümlerin yüklenmesi ve yönetimi için IPv6 (DHCPv6) sunucusu için dinamik ana bilgisayar yapılandırma protokolüne ihtiyaç duyduğundan, bu tür bir yapılandırma belirli bir insan müdahalesi düzeyi gerektirir. DHCPv6 sunucusu, yapılandırma bilgilerini sağladığı düğümlerin bir listesini tutar. Ayrıca, sunucunun her adresin ne kadar süreyle kullanıldığını ve yeniden atanabilir ne zaman kullanılabileceğini bilmesi için durum bilgilerini de saklar.  
  
- **Stateless otomatik yapılandırma.** Bu tür yapılandırmalar küçük kuruluşlar ve bireyler için uygundur. Bu durumda, her ana bilgisayar adreslerini alınan yönlendirici reklamlarının içeriğinden belirler. Adresin ağ kimliği bölümünü tanımlamak için IEEE EUI-64 standardını kullanarak, bağlantıdaki ana bilgisayar adresinin benzersizliğini varsaymak mantıklıdır.  
  
 Adres nasıl belirlenirse belirlensin, düğüm potansiyel adresinin yerel bağlantıya özgü olduğunu doğrulamalıdır. Bu, olası adrese komşu talep iletisi göndererek yapılır. Düğüm herhangi bir yanıt alırsa, adresin zaten kullanımda olduğunu bilir ve başka bir adres belirlemesi gerekir.  
  
## <a name="ipv6-mobility"></a>IPv6 Mobilite  
 Mobil cihazların yaygınlaşması yeni bir gereksinim getirmiştir: Bir cihaz IPv6 Internet'teki konumları rasgele değiştirebilmeli ve hala varolan bağlantıları koruyabilmeli. Bu işlevselliği sağlamak için, bir mobil düğüme her zaman ulaşılabildiği bir ev adresi atanır. Mobil düğüm evdeyken, ev bağlantısına bağlanır ve ev adresini kullanır. Mobil düğüm evden uzaktayken, genellikle yönlendirici olan bir ev aracısı, iletişim kurmakta olduğu mobil düğüm ve düğümler arasında iletiler iletir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
