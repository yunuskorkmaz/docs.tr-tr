---
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91a97807d45d3cafdac0c0608dc9590533b185dc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663440"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<System. Runtime. Caching > öğesi (önbellek ayarları)

Yapılandırma dosyasındaki <xref:System.Runtime.Caching.ObjectCache> `memoryCache` giriş aracılığıyla varsayılan bellek içi uygulama için yapılandırma sağlar.  
  
 \<Yapılandırma >  
\<System. Runtime. Caching >  
  
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
|[\<memoryCache >](memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar

Bu ad alanındaki sınıflar, ASP.net ' deki, ancak `System.Web` derlemeye bağımlılık olmadan önbelleğe alma olanaklarını kullanmanın bir yolunu sunar. Daha fazla bilgi için bkz. [.NET Framework uygulamalarında önbelleğe alma](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  Çıktı önbelleği işlevselliği ve <xref:System.Runtime.Caching> ad alanındaki türler .NET Framework 4 ' te yenidir.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> sınıfına dayalı bir önbelleğin nasıl yapılandırılacağını gösterir. Örnek, bellek önbelleği için `namedCaches` girdinin bir örneğinin nasıl yapılandırılacağını gösterir. Önbellek adı `name` özniteliği "varsayılan" olarak ayarlanarak varsayılan önbellek girişi adına ayarlanır.  
  
`cacheMemoryLimitMegabytes` Özniteliği`physicalMemoryPercentage` ve özniteliği sıfır olarak ayarlanır. Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir. Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.  
  
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

- [\<memoryCache > öğesi (önbellek ayarları)](memorycache-element-cache-settings.md)
