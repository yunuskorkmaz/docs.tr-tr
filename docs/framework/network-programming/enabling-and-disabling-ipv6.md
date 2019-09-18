---
title: IPv6 Etkinleştirme ve Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048570"
---
# <a name="enabling-and-disabling-ipv6"></a>IPv6 Etkinleştirme ve Devre Dışı Bırakma
IPv6 protokolünü kullanmak için, IPv6 'Yı destekleyen bir işletim sistemi sürümü çalıştırdığından ve işletim sisteminin ve ağ sınıflarının düzgün yapılandırıldığından emin olun.  
  
## <a name="configuration-steps"></a>Yapılandırma adımları  
 Aşağıdaki tabloda çeşitli yapılandırma listelenmiştir  
  
|İşletim sistemi IPv6 etkin mi?|Ağ sınıfları IPv6-etkin mi?|Açıklama|  
|-------------------------------------|---------------------------------------|-----------------|  
|Hayır|Hayır|IPv6 adreslerini ayrıştırılabilir.|  
|Hayır|Evet|IPv6 adreslerini ayrıştırılabilir.|  
|Evet|Hayır|, Bilinen olarak işaretlenmemiş ad çözümleme yöntemlerini kullanarak IPv6 adreslerini ayrıştırıp adresleri çözümleyebilir.|  
|Evet|Evet|, Artık kullanılmıyor olarak işaretlenenler dahil tüm yöntemleri kullanarak IPv6 adreslerini ayrıştırıp çözümleyebilir.|  
  
 System.Net ad alanındaki tüm sınıfların IPv6 desteğini etkinleştirmek için, bilgisayar yapılandırma dosyasını veya uygulamanın yapılandırma dosyasını değiştirmeniz gerektiğini unutmayın. Bir uygulamanın yapılandırma dosyası, bilgisayar yapılandırma dosyasına göre önceliğe sahiptir.  
  
 Bilgisayar yapılandırma dosyasının, *Machine. config*, IPv6 desteğinin etkinleştirilmesi için nasıl değiştirileceği hakkında bir örnek için bkz [. nasıl yapılır: IPv6 desteğini](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)etkinleştirmek Için bilgisayar yapılandırma dosyasını değiştirin. Ayrıca, işletim sistemi için IPv6 desteğinin etkinleştirildiğinden emin olun.  
  
 .NET Framework yapılandırma dosyasında aşağıdaki şekilde ayarlanmış bir yapılandırma anahtarı vardır  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 .NET Framework sürüm 1,1 ve önceki sürümlerde **IPv6 etkin** yapılandırma anahtarının değeri, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyelerinin IPv6 adresleri döndürmeyeceğini belirtir.  
  
 .NET Framework sürüm 2,0 ve üzeri için, Windows IPv6 'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyeleri (örneğin <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> , yöntemi) bir sınırlamaya sahip IPv6 adreslerini döndürür. Kullanılmayan DNS <xref:System.Net.Dns?displayProperty=nameWithType> üyeleri (örneğin <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> , yöntemi) IPv6 etkin ayarının yapılandırma dosyasındaki değeri okur ve tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
- [Ağ Ayarları Şeması](../configure-apps/file-schema/network/index.md)
- [\<IPv6 > öğesi (ağ ayarları)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
