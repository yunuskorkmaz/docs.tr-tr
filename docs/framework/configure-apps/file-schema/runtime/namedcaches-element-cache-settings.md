---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153964"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches> Öğesi (Önbellek Ayarları)
Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarları koleksiyonunu belirtir. Özellik, <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> yapılandırma dosyasının bir veya `namedCaches` daha fazla öğesinden yapılandırma ayarlarının toplanmasına başvurur.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.önbelleğe alma>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryÖnbellek>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
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
|`cacheMemoryLimitMegabytes`|Megabaytlarda izin verilen maksimum boyutu belirten bir tamsayı değeri, bir <xref:System.Runtime.Caching.MemoryCache> örneğin büyüyebileceği. Varsayılan değer 0'dır, bu da <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşclarının varsayılan olarak kullanıldığı anlamına gelir.|  
|`name`|Önbelleğin adı.|  
|`physicalMemoryLimitPercentage`|Önbellek tarafından tüketilebilen fiziksel olarak yüklenmiş bilgisayar belleğinin maksimum yüzdesini belirten 0 ile 100 arasında bir tamsayı değeri. Varsayılan değer 0'dır, bu da <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşclarının varsayılan olarak kullanıldığı anlamına gelir.|  
|`pollingInterval`|Önbellek uygulamasının geçerli bellek yükünü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırdığı zaman aralığını gösteren bir değer. Bu değer "HH:MM:SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<>ekleyin](add-element-for-namedcaches.md)|Bellek önbelleği için `namedCaches` koleksiyona adlandırılmış bir önbellek ekler.|  
|[\<açık>](clear-element-for-namedcaches.md)|Bellek önbelleği `namedCaches` için koleksiyonu temizler.|  
|[\<>kaldırmak](remove-element-for-namedcaches.md)|Bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış önbellek girişini kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yapılandırma>](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.|  
|[\<memoryÖnbellek>](memorycache-element-cache-settings.md)|Sınıfı temel alan önbelleği yapılandırmak için kullanılan bir <xref:System.Runtime.Caching.MemoryCache> öğetanımlar.|  
|[\<system.runtime.önbelleğe alma>](system-runtime-caching-element-cache-settings.md)|.NET Framework'de yerleşik olan uygulamalarda çıktı önbelleğe alma uygulamanızı sağlayan türleri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Web.config dosyasının bellek önbelleği yapılandırma `add` `remove` `namedCaches` bölümü, `clear` koleksiyon için öznitelikleri ve öznitelikleri içerebilir. Her `namedCaches` giriş öznitelik tarafından `name` benzersiz olarak tanımlanır.  
  
 Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbellek girişleri örneklerini alabilirsiniz. Varsayılan olarak, yapılandırma dosyasında yalnızca varsayılan önbellek örneği bir girişi vardır. Varsayılan önbellek <xref:System.Runtime.Caching.MemoryCache.Default%2A> örneği, özellikten döndürülen örnektir.  
  
 Ad özniteliğini "varsayılan" olarak ayarlarsanız, öğe varsayılan bellek önbellek örneğini kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `name` özniteliği "varsayılan" olarak ayarlayarak önbelleğin adının varsayılan önbellek giriş adı olarak nasıl ayarlanılabildiği gösterilmektedir.  
  
 Öznitelik `cacheMemoryLimitMegabytes` ve `physicalMemoryPercentage` öznitelik sıfıra ayarlanır. Bu öznitelikleri sıfıra ayarlamak, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma sezgisellerinin kullanıldığı anlamına gelir. Önbellek uygulaması, geçerli bellek yükünü her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırır.  
  
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

- [\<memoryÖnbellek> Öğesi (Önbellek Ayarları)](memorycache-element-cache-settings.md)
