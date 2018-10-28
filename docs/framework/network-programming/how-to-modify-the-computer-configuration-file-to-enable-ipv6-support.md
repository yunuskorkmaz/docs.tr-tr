---
title: 'Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 32aa1c3fa50d5c0486da4ef6799c77ead605b504
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187263"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme
Aşağıdaki kod örneği bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir *machine.config*, IPv6 desteğini etkinleştirmek için. *Machine.config* dosyasının depolandığı *%Windir%\Microsoft.NET\Framework* dizinde Windows yüklendiği klasör. Ayrı bir yoktur *machine.config* altındaki klasörler dosyasında *%Windir%\Microsoft.NET\Framework* bilgisayarda yüklü .NET Framework'ün her sürümü için (örneğin, *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.  
  
 .NET Framework sürüm 1.1 ve önceki değerini **IPv6 etkin** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıf, IPv6 adreslerini döndürür.  
  
 .NET Framework sürüm 2.0 ve üzeri, Windows IPv6, ardından tüm üyelerinin destekliyorsa <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), tek bir kısıtlama olmaksızın IPv6 adreslerini döndürür. Üyeleri geçersiz <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuyun ve yapılandırma dosyasında değer tanınamıyor.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ve sonraki sürümleri için IPv6, varsayılan olarak etkindir. .NET Framework sürüm 1.1 ve önceki sürümler için IPv6, varsayılan olarak devre dışıdır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IPv6 Adresleme](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [Ağ Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<IPv6 > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
