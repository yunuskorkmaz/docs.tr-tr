---
title: 'Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 73408afe9fcb35daa898c08b087a3411a6cb342b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180800"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme
Aşağıdaki kod örneği, IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyası *machine.config'in*nasıl değiştirilebildiğini gösterir. *machine.config* dosyası, Windows'un yüklendiği dizinde *%Windir%\Microsoft.NET\Framework* klasöründe depolanır. Bilgisayarda yüklü olan .NET Framework'ün her sürümü için *%Windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *machine.config* dosyası bulunmaktadır (örneğin, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config).*  
  
 Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.  
  
 .NET Framework sürüm 1.1 ve daha önceki sürümiçin, **ipv6 etkinleştirilmiş** <xref:System.Net.Dns?displayProperty=nameWithType> yapılandırma anahtarının değeri, sınıf üyelerinin IPv6 adreslerini döndürüp döndürmeyeceğini belirtir.  
  
 .NET Framework sürüm 2.0 ve sonrası için, Windows IPv6'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın tüm üyeleri (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntem), IPv6 adreslerini tek bir sınırlamayla döndürecektir. <xref:System.Net.Dns?displayProperty=nameWithType> Sınıfın eski üyeleri (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntem) yapılandırma dosyasındaki değeri okur ve tanır.  
  
> [!NOTE]
> .NET Framework sürüm 2.0 ve sonrası için, IPv6 varsayılan olarak etkinleştirilir. .NET Framework sürüm 1.1 ve daha önceki sürümiçin, IPv6 varsayılan olarak devre dışı bırakılır.  
  
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
- [Ağ Ayarları Şeması](../configure-apps/file-schema/network/index.md)
- [\<ipv6> Elemanı (Ağ Ayarları)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
