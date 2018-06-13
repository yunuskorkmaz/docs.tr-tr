---
title: '&lt;namedCaches&gt; öğesi (önbellek ayarları)'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fac50aedbb11eba40482fab71c912f587d85f855
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744661"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt; öğesi (önbellek ayarları)
Adlandırılmış için yapılandırma ayarlarını koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> örnekleri. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Özelliği, bir veya daha fazla yapılandırma ayarları topluluğunu başvurur `namedCaches` yapılandırma dosyasının öğeleri.  
  
 \<Yapılandırma >  
\< System.Runtime.Caching >  
\<memoryCache >  
\<namedCaches >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>Tür  
 `None`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|En fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> için büyüyebilir. Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.|  
|`name`|Önbellek adı.|  
|`physicalMemoryLimitPercentage`|Önbellek tarafından kullanılabilecek yüklü olan fiziksel bilgisayar belleğini yüzdesinin üst sınırını belirtir 0 ile 100 arasında bir tamsayı değeri. Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.|  
|`pollingInterval`|Daha sonra önbellek uygulaması için önbellek örneğini ayarlamak mutlak ve yüzde tabanlı bellek sınırları göre geçerli bellek yükü karşılaştırır zaman aralığını gösteren bir değer. Bu değer "Ss: dd:" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Adlandırılmış bir önbelleğe ekler `namedCaches` bir önbellek için koleksiyonu.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Temizler `namedCaches` bir önbellek için koleksiyonu.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Bir adlandırılmış önbellek girişi kaldırır `namedCaches` bir önbellek için koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<memoryCache >](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bellek önbelleği yapılandırma bölümü Web.config dosyasının içerebilir `add`, `remove`, ve `clear` için öznitelikler `namedCaches` koleksiyonu. Her `namedCaches` girişi tarafından tanımlanan benzersiz olarak `name` özniteliği.  
  
 Uygulama yapılandırma dosyaları bilgilerinde başvurarak bellek önbellek girişlerinin örneklerini alabilir. Varsayılan olarak, yalnızca varsayılan önbellek örneği yapılandırma dosyasında bir giriş içeriyor. Varsayılan önbellek örneği sunucudan döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> özelliği.  
  
 "Varsayılan" name özniteliği ayarlarsanız, öğe varsayılan bellek önbellek örneği kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ayarlayarak varsayılan önbellek girişi adı önbellek adını ayarlayın gösterilmektedir `name` "varsayılan" özniteliği.  
  
 `cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır. Bu öznitelikler sıfır olarak ayarlandığında anlamına otomatik boyutlandırma buluşsal yöntemler, <xref:System.Runtime.Caching.MemoryCache> sınıfı kullanılır. Önbellek uygulaması mutlak ve yüzde tabanlı bellek sınırları her iki dakikada göre geçerli bellek yükü karşılaştırır.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<memoryCache > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
