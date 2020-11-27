---
title: 'Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme'
description: machine.config, .NET Framework IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını nasıl değiştireceğinizi öğrenin.
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 2c5e3e094eca480a7cab4f7c25cc0fedba196338
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269606"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme

Aşağıdaki kod örneği, IPv6 desteğinin etkinleştirilmesi için *machine.config*, bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir. *machine.config* dosyası, Windows 'un yüklendiği dizindeki *%windir%\Microsoft.NET\Framework* klasöründe depolanır. Bilgisayarda yüklü olan .NET Framework her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *machine.config* dosyası vardır (örneğin, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.  
  
 .NET Framework sürüm 1,1 ve önceki sürümlerde **IPv6 etkin** yapılandırma anahtarının değeri, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyelerinin IPv6 adresleri döndürmeyeceğini belirtir.  
  
 .NET Framework sürüm 2,0 ve üzeri için, Windows IPv6 'yı destekliyorsa, sınıfın tüm üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi) bir sınırlamaya sahip IPv6 adreslerini döndürür. Sınıfın kullanılmayan üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) yapılandırma dosyasındaki değeri okur ve tanır.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ve üzeri için IPv6 varsayılan olarak etkindir. .NET Framework sürüm 1,1 ve önceki sürümlerde IPv6 varsayılan olarak devre dışıdır.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>
    ……………  
    </settings>  
    ………………  
</system.net>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IPv6 Adresleme](ipv6-addressing.md)
- [Ağ ayarları şeması](../configure-apps/file-schema/network/index.md)
- [\<ipv6> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
