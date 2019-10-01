---
title: <performanceCounter> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 3fe6b19d0055aafad859b55960800d9786d7fa08
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697996"
---
# <a name="performancecounter-element-network-settings"></a>\<performanceCounter > öğesi (ağ ayarları)
Ağ performans sayaçlarını etkinleştirilir veya devre dışı bırakır.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<performanceCounters >**  
  
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
|`enabled`|Ağ performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Ayarlar](settings-element-network-settings.md)|@No__t-0 ad alanı için temel ağ seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
 Ağ performans sayaçlarının kullanılacak yapılandırma dosyasında etkinleştirilmesi gerekir. Tüm ağ performans sayaçları, yapılandırma dosyasında tek bir ayarla etkin veya devre dışı bırakıldı. Bireysel ağ performans sayaçları etkinleştirilemez veya devre dışı bırakılamaz. Belirli ağ performans sayaçları hakkında daha fazla bilgi için bkz. [ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking).  
  
 Varsayılan değer ağ performans sayaçlarının devre dışı bırakıldığını unutmayın.  
  
 @No__t-0 özelliği, geçerli yapılandırma dosyalarından **etkin** özniteliğin geçerli değerini almak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ağ performans sayaçlarını etkinleştirmek üzere <xref:System.Net> ve ilgili ad alanlarının nasıl yapılandırılacağını gösterir.  
  
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
- [Ağ Ayarları Şeması](index.md)
- [Ağ performans sayaçları](../../../debug-trace-profile/performance-counters.md#networking)
