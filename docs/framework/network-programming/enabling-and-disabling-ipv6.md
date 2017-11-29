---
title: "Etkinleştirme ve IPv6 devre dışı bırakma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9edb87cf1ee35ac6848a478552cf8d0732177a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-and-disabling-ipv6"></a>Etkinleştirme ve IPv6 devre dışı bırakma
IPv6 protokolünü kullanmak için bir IPv6'yı destekleyen işletim sistemi sürümünü çalıştırdığından emin olun ve işletim sistemi ve ağ sınıfları düzgün yapılandırıldığından emin olun.  
  
## <a name="configuration-steps"></a>Yapılandırma adımları  
 Aşağıdaki tabloda çeşitli yapılandırmaları listeler  
  
|İşletim sistemi IPv6 etkinleştirilmiş mi?|Ağ, IPv6 özellikli sınıfları?|Açıklama|  
|-------------------------------------|---------------------------------------|-----------------|  
|Hayır|Hayır|IPv6 adresleri ayrıştıramıyor.|  
|Hayır|Evet|IPv6 adresleri ayrıştıramıyor.|  
|Evet|Hayır|IPv6 adresleri ayrıştırabilir ve ad çözümleme yöntemleri geçersiz işaretlenmemiş kullanarak IPv6 adresleri çözümleyecek.|  
|Evet|Evet|Ayrıştırılamıyor ve geçersiz olarak işaretlenmiş dahil olmak üzere tüm yöntemleri kullanarak IPv6 adresleri çözümleyecek kullanabilirsiniz.|  
  
 System.Net ad alanındaki tüm sınıfları IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyası veya uygulama için yapılandırma dosyası değiştirmelisiniz olduğunu unutmayın. Bir uygulama için yapılandırma dosyası bilgisayar yapılandırma dosyası önceliğe sahiptir.  
  
 Bilgisayar yapılandırma dosyasını değiştirme konusunda bir örnek için *machine.config*, etkinleştirmek için IPv6 desteği bkz [nasıl yapılır: IPv6'yı destekleyen etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Ayrıca, IPv6 desteği için işletim sistemini etkinleştirildiğinden emin olun.  
  
 .NET Framework yapılandırma dosyasında aşağıdaki gibi ayarlayın yapılandırma anahtarı sahiptir  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 .NET Framework sürüm 1.1 ve önceki değeri için **etkin IPv6** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı IPv6 adresleri döndürür.  
  
 .NET Framework sürüm 2.0 ve daha sonra Windows IPv6 sonra üyeleri destekliyorsa için <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), IPv6 adresleriyle bir sınırlama döndürür. Eski DNS üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuma ve yapılandırma dosyasındaki IPv6 etkin ayarı için değer algılar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Protokolü sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Yuva](../../../docs/framework/network-programming/sockets.md)  
 [Ağ Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<IPv6 > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
