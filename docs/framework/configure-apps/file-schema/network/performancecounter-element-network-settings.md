---
title: <performanceCounters> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 584bdafbbd60303401cbc6ad96b8654fe11c7077
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756266"
---
# <a name="performancecounters-element-network-settings"></a>\<performanceCounters> Öğesi (Ağ Ayarları)

Ağ performans sayaçlarını etkinleştirilir veya devre dışı bırakır.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Ağ performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer: `false`.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ayarlar](settings-element-network-settings.md)|Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
 Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir. Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı. Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz. Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).  
  
 Varsayılan değer ağ performans sayaçlarının devre dışı bırakıldığını unutmayın.  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>Özelliği, geçerli yapılandırma dosyalarından **etkin** özniteliğin geçerli değerini almak için kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Net> ağ performans sayaçlarını etkinleştirmek için ve ilgili ad alanlarının nasıl yapılandırılacağını gösterir.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [Ağ ayarları şeması](index.md)
- [Ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
