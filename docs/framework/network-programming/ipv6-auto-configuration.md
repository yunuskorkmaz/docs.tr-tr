---
title: "IPv6 otomatik yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0332bca146041aa955ea000cfeee78d3f5287036
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-auto-configuration"></a>IPv6 otomatik yapılandırma
IPv6 için önemli bir hedef düğümü Tak ve Kullan desteklemektir. Diğer bir deyişle, bir IPv6 ağında bir düğüm takın ve insan müdahalesi otomatik olarak yapılandırılması mümkün olmalıdır.  
  
## <a name="type-of-auto-configuration"></a>Otomatik yapılandırma türü  
 IPv6 otomatik yapılandırma aşağıdaki türlerini destekler:  
  
-   **Durum bilgisi olan otomatik yapılandırma**. IPv6 için Dinamik Ana Bilgisayar Yapılandırma Protokolü gerektiğinden bu tür bir yapılandırma belirli bir düzeyde insan etkileşimi gerektirir (DHCPv6) sunucusu yükleme ve yönetim düğümü. DHCPv6 sunucusu için yapılandırma bilgilerini sağlayan düğümleri listesini tutar. Ne kadar her adresi kullanılıyor ve ne zaman yeniden atama için kullanılabilir olabilir sunucuya bilmesi için de durum bilgisini tutar.  
  
-   **Durum bilgisiz otomatik yapılandırmanın**. Bu tür bir yapılandırma küçük kuruluşlar ve kişiler için uygundur. Bu durumda, her konak, alınan yönlendirici reklam içeriğini adresinden belirler. Adresin ağ kimliği bölümünü tanımlamak için IEEE EUI-64 standart kullanarak ana bilgisayar adresi bağlantıyı benzersizliğini varsaymak makul değildir.  
  
 Adres nasıl belirlendiğinden bağımsız olarak düğümü olası adresini yerel bağlantısını benzersiz olduğunu doğrulamanız gerekir. Bu komşu isteği göndererek yapılır olası adresine ileti. Düğüm herhangi bir yanıt alırsa, adresi zaten kullanılıyor ve başka bir adresini belirlemelidir bilir.  
  
## <a name="ipv6-mobility"></a>IPv6 Mobility  
 Mobil aygıtların artışı yeni gereksinimi sunulan: bir aygıtı rasgele IPv6 Internet üzerindeki konumlara değiştirmek ve hala var olan bağlantıların sürdürmek kurabilmesi gerekir. Bu işlevsellik sağlamak için mobil bir düğüme, bu her zaman ulaşılabilen ev adresi atanır. Mobil düğüm evde olduğunda giriş bağlantısı bağlanır ve ev adresini kullanır. Mobil düğüm giriş uzağa doğru olduğunda, genellikle bir yönlendirici olduğundan, bir ev Aracısı iletileri mobil düğümü ve hangi bağlanıyor düğümler arasında aktarır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Protokolü sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Yuva](../../../docs/framework/network-programming/sockets.md)
