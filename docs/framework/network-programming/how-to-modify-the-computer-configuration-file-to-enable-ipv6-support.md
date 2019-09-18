---
title: 'Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 362e7af36d214df9f0454479e25a80af9d440b2b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048284"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme
Aşağıdaki kod örneği, IPv6 desteğinin etkinleştirilmesi için *Machine. config*bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir. *Machine. config* dosyası, Windows 'un yüklendiği dizindeki *%windir%\Microsoft.NET\Framework* klasöründe depolanır. Bilgisayarda yüklü .NET Framework her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *Machine. config* dosyası bulunur (örneğin, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\ Machine. config*).  
  
 Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.  
  
 .NET Framework sürüm 1,1 ve önceki sürümlerde **IPv6 etkin** yapılandırma anahtarının değeri, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyelerinin IPv6 adresleri döndürmeyeceğini belirtir.  
  
 .NET Framework sürüm 2,0 ve üzeri için, Windows IPv6 'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın tüm üyeleri (örneğin <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> , yöntemi) bir sınırlamaya sahip IPv6 adreslerini döndürür. <xref:System.Net.Dns?displayProperty=nameWithType> Sınıfın kullanılmayan üyeleri (örneğin <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> , yöntemi) yapılandırma dosyasındaki değeri okur ve tanır.  
  
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
<system.net>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IPv6 Adresleme](ipv6-addressing.md)
- [Ağ Ayarları Şeması](../configure-apps/file-schema/network/index.md)
- [\<IPv6 > öğesi (ağ ayarları)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
