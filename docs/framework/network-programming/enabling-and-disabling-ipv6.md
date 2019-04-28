---
title: IPv6 Etkinleştirme ve Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 73dee0cb57674c8a2fa4ba2246162870ab1e3a10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643107"
---
# <a name="enabling-and-disabling-ipv6"></a>IPv6 Etkinleştirme ve Devre Dışı Bırakma
IPv6 protokolü kullanmak için bir IPv6 destekleyen bir işletim sistemi sürümünü çalıştırdığından emin olun ve işletim sistemi ve ağ sınıfları düzgün yapılandırıldığından emin olun.  
  
## <a name="configuration-steps"></a>Yapılandırma adımları  
 Aşağıdaki tabloda çeşitli yapılandırmalarını listeler  
  
|İşletim sistemi IPv6 özellikli?|Ağ, IPv6 özellikli sınıfları?|Açıklama|  
|-------------------------------------|---------------------------------------|-----------------|  
|Hayır|Hayır|IPv6 adresleri ayrıştırabilirsiniz.|  
|Hayır|Evet|IPv6 adresleri ayrıştırabilirsiniz.|  
|Evet|Hayır|IPv6 adresleri ayrıştırabilir ve eski işaretlenmemiş ad çözümleme yöntemleri kullanarak IPv6 adresleri çözümlemek.|  
|Evet|Evet|Ayrıştırabilir ve IPv6 adresleri artık kullanılmıyor olarak işaretlendiğinden dahil olmak üzere tüm yöntemleri kullanarak çözün.|  
  
 System.Net ad alanındaki tüm sınıflar için IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyası veya uygulama için yapılandırma dosyasını değiştirmeniz gerekir olduğunu unutmayın. Bir uygulama yapılandırma dosyası, bilgisayar yapılandırma dosyası üzerinde önceliğe sahiptir.  
  
 Bilgisayar yapılandırma dosyasını değiştirme ilişkin bir örnek için *machine.config*, etkinleştirmek için IPv6 desteği bkz [nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Ayrıca, IPv6 desteği için işletim sistemi etkinleştirildiğinden emin olun.  
  
 .NET Framework sahip bir yapılandırma dosyasında şu şekilde ayarlanan bir yapılandırma anahtarı  
  
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
  
 .NET Framework sürüm 1.1 ve önceki değerini **IPv6 etkin** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıf, IPv6 adreslerini döndürür.  
  
 .NET Framework sürüm 2.0 ve üzeri, Windows IPv6 sonra üyeleri destekliyorsa <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), tek bir kısıtlama olmaksızın IPv6 adreslerini döndürür. Geçersiz DNS üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuyun ve yapılandırma dosyasında IPv6 etkin ayarı için değer tanınamıyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [Yuvalar](../../../docs/framework/network-programming/sockets.md)
- [Ağ Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [\<IPv6 > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
