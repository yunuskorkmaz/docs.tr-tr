---
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153860"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<system.runtime.cacching> Öğesi (Önbellek Ayarları)

Yapılandırma dosyasındaki <xref:System.Runtime.Caching.ObjectCache> `memoryCache` giriş aracılığıyla varsayılan bellek içi uygulama yapılandırmasını sağlar.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.önbelleğe alma>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler

`None`  

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<memoryÖnbellek>](memorycache-element-cache-settings.md)|Sınıfı temel alan önbelleği yapılandırmak için kullanılan bir <xref:System.Runtime.Caching.MemoryCache> öğetanımlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yapılandırma>](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar

Bu ad alanındaki sınıflar, ASP.NET'daki gibi önbelleğe alma olanaklarını kullanmanın `System.Web` bir yolunu sağlar, ancak derlemeye bağımlılık olmadan. Daha fazla bilgi için [.NET Framework Applications'da Önbelleğe Alma'ya](../../../performance/caching-in-net-framework-applications.md)bakın.  
  
> [!NOTE]
> <xref:System.Runtime.Caching> Ad alanındaki çıktı önbelleğe alma işlevi ve türleri .NET Framework 4'te yenidir.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> sınıfa dayalı bir önbelleğin nasıl yapılandırılabildiğini gösterir. Örnek, bellek önbelleği için `namedCaches` giriş örneğinin nasıl yapılandırılabildiğini gösterir. Önbelleğin adı, `name` özniteliği "Varsayılan" olarak ayarlayarak varsayılan önbellek giriş adı olarak ayarlanır.  
  
Öznitelik `cacheMemoryLimitMegabytes` ve `physicalMemoryPercentage` öznitelik sıfıra ayarlanır. Bu öznitelikleri sıfıra <xref:System.Runtime.Caching.MemoryCache> ayarlamak, otomatik boyutlandırma sezgisellerinin varsayılan olarak kullanıldığı anlamına gelir. Önbellek uygulaması, geçerli bellek yükünü her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırmalıdır.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<memoryÖnbellek> Öğesi (Önbellek Ayarları)](memorycache-element-cache-settings.md)
