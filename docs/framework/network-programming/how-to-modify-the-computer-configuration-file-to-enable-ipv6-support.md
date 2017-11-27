---
title: "Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 696aeb619f14a5ebe9a760cbd78a0d0fa876edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme
Aşağıdaki kod örneğinde bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir *machine.config*, IPv6 desteğini etkinleştirmek için. *Machine.config* dosya depolanır *%Windir%\Microsoft.NET\Framework* Windows yüklendiği klasörü dizininde. Ayrı bir yoktur *machine.config* altındaki klasörler dosyasında *%Windir%\Microsoft.NET\Framework* her bilgisayarda yüklü .NET Framework sürümü için (örneğin, *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.  
  
 .NET Framework sürüm 1.1 ve önceki değeri için **etkin IPv6** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı IPv6 adresleri döndürür.  
  
 .NET Framework sürüm 2.0 ve daha sonra Windows IPv6 sonra tüm üyeleri destekliyorsa için <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), IPv6 adresleriyle bir sınırlama döndürür. Kullanımdan kalktı üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuma ve yapılandırma dosyasındaki değer tanınamıyor.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ve sonraki sürümleri için IPv6 varsayılan olarak etkindir. .NET Framework sürüm 1.1 ve önceki sürümler için IPv6 varsayılan olarak devre dışıdır.  
  
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
 [IPv6 adresi](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [Ağ Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<IPv6 > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
