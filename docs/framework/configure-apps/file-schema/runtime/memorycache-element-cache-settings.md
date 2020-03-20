---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153990"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryÖnbellek> Öğesi (Önbellek Ayarları)
Sınıfı temel alan önbelleği yapılandırmak için kullanılan bir <xref:System.Runtime.Caching.MemoryCache> öğetanımlar. Sınıf, <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> önbelleği yapılandırmak için kullanabileceğiniz bir [memoryCache](memorycache-element-cache-settings.md) öğesini tanımlar. <xref:System.Runtime.Caching.MemoryCache> Sınıfın birden çok örneği tek bir uygulamada kullanılabilir. Yapılandırma `memoryCache` dosyasındaki her öğe, adlandırılmış <xref:System.Runtime.Caching.MemoryCache> bir örneğin ayarlarını içerebilir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.önbelleğe alma>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryÖnbellek>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a>Tür  
 <xref:System.Runtime.Caching.MemoryCache>Sınıfı.  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Megabaytlarda, bir <xref:System.Runtime.Caching.MemoryCache> nesnenin bir örneğinin büyüyebileceği maksimum bellek boyutu. Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma buluşsal larının varsayılan olarak kullanıldığı anlamına gelir.|  
|`Name`|Önbellek yapılandırmasının adı.|  
|`PhysicalMemoryLimitPercentage`|Önbellek tarafından kullanılabilecek fiziksel bellek yüzdesi. Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma buluşsal larının varsayılan olarak kullanıldığı anlamına gelir.|  
|`PollingInterval`|Önbellek uygulamasının geçerli bellek yükünü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırdığı zaman aralığını gösteren bir değer. Değer "HH:MM:SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|`namedCache` Örnek için yapılandırma ayarları koleksiyonu içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yapılandırma>](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.|  
|[\<system.runtime.önbelleğe alma>](system-runtime-caching-element-cache-settings.md)|.NET Framework'de yerleşik olan uygulamalarda çıktı önbelleğe alma uygulamanızı sağlayan türleri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf <xref:System.Runtime.Caching.MemoryCache> soyut <xref:System.Runtime.Caching.ObjectCache> sınıfın somut bir uygulamasıdır. <xref:System.Runtime.Caching.MemoryCache> Sınıfın örnekleri, uygulama yapılandırma dosyalarından yapılandırma bilgileriyle birlikte sağlanabilir. [memoryCache](memorycache-element-cache-settings.md) yapılandırma bölümü `namedCaches` bir yapılandırma koleksiyonu içerir.  
  
 Bellek tabanlı önbellek nesnesi baş harfe döndüğünde, `namedCaches` önce bellek önbelleği oluşturucuya geçirilen parametredeki adla eşleşen bir giriş bulmaya çalışır. Bir `namedCaches` giriş bulunursa, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.  
  
 Başlatma işlemi daha sonra, yapılandırma bilgilerinin isteğe bağlı topunu kullanarak yapılandırma girdilerinin geçersiz kılınıp geçersiz kılınmadığını belirler. Ad/değer çifti koleksiyonunda aşağıdaki değerlerden herhangi birini geçerseniz, bu değerler yapılandırma dosyasından elde edilen bilgileri geçersiz kılar:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Runtime.Caching.MemoryCache> `name` özniteliği "Varsayılan" olarak ayarlayarak nesnenin adının varsayılan önbellek nesnesi adına nasıl ayarlanılabildiği gösterilmektedir.  
  
 Öznitelik `cacheMemoryLimitMegabytes` ve `physicalMemoryLimitPercentage` öznitelik sıfıra ayarlanır. Bu öznitelikleri sıfıra <xref:System.Runtime.Caching.MemoryCache> ayarlamak, otomatik boyutlandırma sezgisellerinin varsayılan olarak kullanıldığı anlamına gelir. Önbellek uygulaması, geçerli bellek yükünü her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırmalıdır.  
  
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

- <xref:System.Runtime.Caching.MemoryCache>
- [\<system.runtime.cacching> Öğesi (Önbellek Ayarları)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches> Öğesi (Önbellek Ayarları)](namedcaches-element-cache-settings.md)
