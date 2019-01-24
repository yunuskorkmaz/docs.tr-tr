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
ms.openlocfilehash: a824e958a2b75b28aa66a15212e0276d6c127739
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536535"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt; öğesi (önbellek ayarları)
Yapılandırma ayarları için adlandırılmış bir koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> örnekleri. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Özelliği, bir veya daha fazla yapılandırma ayarları koleksiyonu başvurur `namedCaches` yapılandırma dosyasının öğeleri.  
  
 \<Yapılandırma >  
\< System.Runtime.Caching >  
\<memoryCache>  
\<namedCaches>  
  
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
|`cacheMemoryLimitMegabytes`|Megabayt cinsinden izin verilen boyut sınırını belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> kadar büyüyebilir. Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0 ' dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.|  
|`name`|Önbellek adı.|  
|`physicalMemoryLimitPercentage`|Önbelleği tarafından tüketilebilecek yüklü olan fiziksel bilgisayar belleğini en yüksek yüzdesi belirten bir tamsayı değeri 0 ile 100 arasında. Varsayılan değer otomatik boyutlandırma buluşsal yöntemler, yani 0 ' dır <xref:System.Runtime.Caching.MemoryCache> sınıfı, varsayılan olarak kullanılır.|  
|`pollingInterval`|Daha sonra önbellek uygulaması geçerli bellek yükü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarını karşı karşılaştırır zaman aralığını belirten bir değer. Bu değer, "Ss" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Adlandırılmış bir önbelleğe ekler `namedCaches` koleksiyonu için bir önbellek.|  
|[\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Temizler `namedCaches` koleksiyonu için bir önbellek.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Bir adlandırılmış önbellek girişi kaldırır `namedCaches` koleksiyonu için bir önbellek.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bellek önbelleğini yapılandırma bölümü Web.config dosyasının içerebilir `add`, `remove`, ve `clear` özniteliklerini `namedCaches` koleksiyonu. Her `namedCaches` giriş tarafından benzersiz şekilde tanımlanır `name` özniteliği.  
  
 Uygulama yapılandırma dosyaları bilgileri başvurarak bellek önbellek girişlerinin yinelenmesini örnekleri alabilirsiniz. Varsayılan olarak, yalnızca varsayılan önbellek örneği yapılandırma dosyasında bir girdi içeriyor. Varsayılan önbellek örneği öğesinden döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> özelliği.  
  
 "Varsayılan" ad özniteliğini ayarlarsanız, öğe varsayılan bellek önbellek örneği kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önbelleğin adını varsayılan önbellek girişi adına ayarlayarak ayarlamak gösterilmektedir `name` "varsayılan" özniteliği.  
  
 `cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryPercentage` öznitelik sıfır olarak ayarlanır. Bu öznitelik sıfır olarak ayarlandığında anlamına otomatik boyutlandırma buluşsal yöntemler, <xref:System.Runtime.Caching.MemoryCache> sınıfı kullanılır. Önbellek uygulaması geçerli bellek yükü mutlak ve yüzde tabanlı bellek sınırlarını her iki dakikada karşı karşılaştırır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [\<memoryCache > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
