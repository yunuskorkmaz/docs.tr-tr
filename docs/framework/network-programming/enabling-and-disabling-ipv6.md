---
title: IPv6 Etkinleştirme ve Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048570"
---
# <a name="enabling-and-disabling-ipv6"></a>IPv6 Etkinleştirme ve Devre Dışı Bırakma
IPv6 protokolünü kullanmak için, IPv6'yı destekleyen işletim sisteminin bir sürümünü çalıştırdığınızdan emin olun ve işletim sistemi ve ağ sınıflarının düzgün şekilde yapılandırıldığından emin olun.  
  
## <a name="configuration-steps"></a>Yapılandırma Adımları  
 Aşağıdaki tabloda çeşitli yapılandırmalar listele  
  
|İşletim sistemi IPv6 etkin?|Ağ sınıfları IPv6 etkin?|Açıklama|  
|-------------------------------------|---------------------------------------|-----------------|  
|Hayır|Hayır|IPv6 adreslerini ayrışdırabilir.|  
|Hayır|Evet|IPv6 adreslerini ayrışdırabilir.|  
|Evet|Hayır|IPv6 adreslerini ayrışdırabilir ve iPv6 adreslerini eski işaretlenmemiş ad çözümleme yöntemlerini kullanarak çözümleyebilir.|  
|Evet|Evet|IPv6 adreslerini, eski işaretlenmiş olanlar da dahil olmak üzere tüm yöntemleri kullanarak ayrıştabilir ve çözebilir.|  
  
 System.Net ad alanındaki tüm sınıflar için IPv6 desteğini etkinleştirmek için, bilgisayar yapılandırma dosyasını veya uygulama nın yapılandırma dosyasını değiştirmeniz gerektiğini unutmayın. Bir uygulamanın yapılandırma dosyasının bilgisayar yapılandırma dosyasından önceliği vardır.  
  
 Bilgisayar yapılandırma dosyası, *machine.config,* Ipv6 desteği sağlamak için nasıl değiştirin bir örnek için [bkz.](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md) Ayrıca, işletim sistemi için IPv6 desteğinin etkin olduğundan emin olun.  
  
 .NET Framework'ün bir yapılandırma dosyasında aşağıdaki gibi ayarlanmış bir yapılandırma anahtarı vardır  
  
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
  
 .NET Framework sürüm 1.1 ve daha önceki sürümiçin, **ipv6 etkinleştirilmiş** <xref:System.Net.Dns?displayProperty=nameWithType> yapılandırma anahtarının değeri, sınıf üyelerinin IPv6 adreslerini döndürüp döndürmeyeceğini belirtir.  
  
 .NET Framework sürüm 2.0 ve sonrası için, Windows IPv6'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyeleri (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntem) IPv6 adreslerini tek bir sınırlamayla döndürecektir. DNS'nin <xref:System.Net.Dns?displayProperty=nameWithType> eski üyeleri (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntem) ipv6 etkin ayar için yapılandırma dosyasındaki değeri okur ve tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
- [Ağ Ayarları Şeması](../configure-apps/file-schema/network/index.md)
- [\<ipv6> Elemanı (Ağ Ayarları)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
