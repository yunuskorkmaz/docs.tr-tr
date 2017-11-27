---
title: "&lt;System.Runtime.Caching&gt; öğesi (önbellek ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13d19560e8d8fbf9254f8baea3811f5d29832dc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a>&lt;System.Runtime.Caching&gt; öğesi (önbellek ayarları)
Varsayılan bellek içi için yapılandırma sağlar <xref:System.Runtime.Caching.ObjectCache> uygulaması aracılığıyla `memoryCache` yapılandırma dosyasındaki girişi.  
  
 \<Yapılandırma >  
\<System.Runtime.Caching >  
  
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
|[\<memoryCache >](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Ortak dil çalışma zamanı tarafından kullanılan her yapılandırma dosyası kök öğesi belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu ad alanındaki sınıflar üzerinde gelenler ASP.NET, ancak bir bağımlılık önbelleğe alma özelliklerini kullanabilmeniz için bir yol sağlama `System.Web` derleme. Daha fazla bilgi için bkz: [.NET Framework uygulamalarında önbelleğe alma](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  Çıktı önbelleği işlevselliği ve türlerinde <xref:System.Runtime.Caching> ad yeni [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek temel alan bir önbellek yapılandırma gösterir <xref:System.Runtime.Caching.MemoryCache> sınıfı. Örnek bir örneğini yapılandırın gösterilmektedir `namedCaches` önbellek girişi. Önbellek adı ayarlayarak varsayılan önbellek girişi adına ayarlanır `name` "varsayılan" özniteliği.  
  
 `cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır. Bu öznitelikler sıfır olarak ayarlandığında <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır. Önbellek uygulaması mutlak ve yüzde tabanlı bellek sınırları her iki dakikada göre geçerli bellek yükü karşılaştırmanız gerekir.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<memoryCache > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
