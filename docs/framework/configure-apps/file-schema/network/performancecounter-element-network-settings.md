---
title: '&lt;performanceCounter&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: ea0eba097505741aba31bce4f23e0cc9ca1d4608
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712489"
---
# <a name="ltperformancecountergt-element-network-settings"></a>&lt;performanceCounter&gt; öğesi (ağ ayarları)
Etkinleştirir veya ağ performans sayaçları devre dışı bırakır.  
  
 \<Yapılandırma >  
\<system.net>  
\<Ayarlar >  
\<performanceCounters >  
  
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
|`enabled`|Ağ performans sayaçlarının etkin olup olmadığını belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
 Ağ performans sayaçları yapılandırma dosyasında kullanılacak etkinleştirilmesi gerekir. Tüm ağ performans sayaçları etkin veya yapılandırma dosyasında tek bir ayarı ile devre dışı. Ağ performans sayaçları tek etkin veya devre dışı. Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).  
  
 Ağ performans sayaçları devre dışı bırakıldı varsayılan değerdir.  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Özelliği, geçerli değerini almak için kullanılabilir **etkin** ilgili yapılandırma dosyaları özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.Net> ve ilgili ağ performans sayaçları etkinleştirmek için ad alanları.  
  
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
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [Ağ performans sayaçları](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
