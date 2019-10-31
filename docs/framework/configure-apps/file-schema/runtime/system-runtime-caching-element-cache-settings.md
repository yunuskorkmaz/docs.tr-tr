---
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115513"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<System. Runtime. Caching > öğesi (önbellek ayarları)

Yapılandırma dosyasındaki `memoryCache` girişi aracılığıyla varsayılan bellek içi <xref:System.Runtime.Caching.ObjectCache> uygulama için yapılandırma sağlar.  
  
[ **\<configuration >** ](../configuration-element.md) \
**System. Runtime. caching &nbsp;&nbsp;\<**  
  
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
|[\<memoryCache >](memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar

Bu ad alanındaki sınıflar, ASP.NET ' deki, ancak `System.Web` derlemesinde bir bağımlılık olmadan önbelleğe alma olanaklarını kullanmanın bir yolunu sunar. Daha fazla bilgi için bkz. [.NET Framework uygulamalarında önbelleğe alma](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Çıktı önbelleği işlevselliği ve <xref:System.Runtime.Caching> ad alanındaki türler .NET Framework 4 ' te yenidir.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> sınıfına dayalı bir önbelleğin nasıl yapılandırılacağını gösterir. Örnek, bellek önbelleği için `namedCaches` girişinin bir örneğinin nasıl yapılandırılacağını gösterir. Önbelleğin adı, `name` özniteliği "default" olarak ayarlanarak varsayılan önbellek girişi adına ayarlanır.  
  
`cacheMemoryLimitMegabytes` özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır. Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir. Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.  
  
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
