---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 25e87aa9fa4e56c5042eb25c41f6cfe1b65aea24
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266383"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache > öğesi (önbellek ayarları)
Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı. <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Sınıfı tanımlayan bir [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) önbelleğini yapılandırmak için kullanabileceğiniz bir öğesi. Birden çok örneğini <xref:System.Runtime.Caching.MemoryCache> sınıfı tek bir uygulama içinde kullanılabilir. Her `memoryCache` öğesi yapılandırma dosyasında bir adlandırılmış için ayarları içerebilir <xref:System.Runtime.Caching.MemoryCache> örneği.  
  
 \<Yapılandırma >  
\<System.Runtime.Caching >  
\<memoryCache>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a>Tür  
 <xref:System.Runtime.Caching.MemoryCache> sınıf.  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Megabayt cinsinden en yüksek bellek boyutu, örneği bir <xref:System.Runtime.Caching.MemoryCache> nesne büyüyebileceği. Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın autosize buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`Name`|Önbellek yapılandırmasının adı.|  
|`PhysicalMemoryLimitPercentage`|Önbelleği tarafından kullanılan fiziksel bellek yüzdesi. Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın autosize buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`PollingInterval`|Daha sonra önbellek uygulaması geçerli bellek yükü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarını karşı karşılaştırır zaman aralığını belirten bir değer. "Ss" biçiminde girilen değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Yapılandırma ayarları koleksiyonu içeren `namedCache` örneği.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.Runtime.Caching >](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Çıktı önbelleği içinde yerleşik olan uygulamalarda uygulama sağlayan türler içerir [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Runtime.Caching.MemoryCache> Sınıf, soyut bir somut uygulaması <xref:System.Runtime.Caching.ObjectCache> sınıfı. Örneklerini <xref:System.Runtime.Caching.MemoryCache> sınıfı, uygulama yapılandırma dosyaları yapılandırma bilgileriyle sağlanabilir. [MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) yapılandırma bölümü içeren bir `namedCaches` yapılandırma koleksiyonu.  
  
 Bir bellek tabanlı önbellek nesnesi başlatılırken, ilk bulmaya çalışır bir `namedCaches` bellek önbellek oluşturucuya geçirilen parametre adıyla eşleşen girişi. Varsa bir `namedCaches` girişi bulundu, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.  
  
 Başlatma işlemi, ardından herhangi bir yapılandırma girdileri, oluşturucuda isteğe bağlı yapılandırma bilgilerini ad/değer çiftleri koleksiyonu kullanarak geçersiz kılınmış olup olmadığını belirler. Aşağıdaki değerlerden herhangi bir ad/değer çifti koleksiyonu geçirirseniz, bu değerler yapılandırma dosyasından alınan bilgilerle geçersiz kıl:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adını ayarlama işlemi gösterilmektedir <xref:System.Runtime.Caching.MemoryCache> ayarlayarak varsayılan önbellek nesnesi adı nesnesine `name` "varsayılan" özniteliği.  
  
 `cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryLimitPercentage` öznitelik sıfır olarak ayarlanır. Bu öznitelik sıfır olarak ayarlandığında <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır. Önbellek uygulaması, iki dakikada mutlak ve yüzde tabanlı bellek sınırlarını karşı geçerli bellek yükü karşılaştırmanız gerekir.  
  
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
- <xref:System.Runtime.Caching.MemoryCache>
- [\<System.Runtime.Caching > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)
- [\<namedCaches > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
