---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 9cedd462aa539745ddab844dff158912914cb024
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663574"
---
# <a name="namedcaches-element-cache-settings"></a>\<Namedönbellekler > öğesi (önbellek ayarları)
Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarları koleksiyonunu belirtir. Özelliği yapılandırma dosyasının bir veya daha fazla `namedCaches` öğesinden yapılandırma ayarları koleksiyonuna başvurur. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>  
  
 \<Yapılandırma >  
\<System. Runtime. Caching >  
\<memoryCache >  
\<Namedönbellekler >  
  
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
|`cacheMemoryLimitMegabytes`|Bir örneğinin bir <xref:System.Runtime.Caching.MemoryCache> örneğinin büyüyebileceği en fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri. Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`name`|Önbelleğin adı.|  
|`physicalMemoryLimitPercentage`|0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri. Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`pollingInterval`|Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer. Bu değer "HH: MM: SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<> Ekle](add-element-for-namedcaches.md)|Bir bellek önbelleği için `namedCaches` koleksiyona adlandırılmış bir önbellek ekler.|  
|[\<> Temizle](clear-element-for-namedcaches.md)|Bir bellek önbelleğinin koleksiyonunu temizler. `namedCaches`|  
|[\<> Kaldır](remove-element-for-namedcaches.md)|Bir bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<memoryCache >](memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Web. config dosyasının bellek önbelleği `add`yapılandırması bölümü `namedCaches` koleksiyon için, `remove`ve `clear` özniteliklerini içerebilir. Her `namedCaches` giriş, `name` öznitelik tarafından benzersiz şekilde tanımlanır.  
  
 Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbelleği girdilerinin örneklerini alabilirsiniz. Varsayılan olarak, yalnızca varsayılan önbellek örneğinin yapılandırma dosyasında bir girişi vardır. Varsayılan önbellek örneği <xref:System.Runtime.Caching.MemoryCache.Default%2A> özelliğinden döndürülen örneğidir.  
  
 Name özniteliğini "default" olarak ayarlarsanız, öğesi varsayılan bellek önbelleği örneğini kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `name` özniteliğini "default" olarak ayarlayarak önbelleğin adının varsayılan önbellek girişi adına nasıl ayarlanacağını gösterir.  
  
 `cacheMemoryLimitMegabytes` Özniteliği`physicalMemoryPercentage` ve özniteliği sıfır olarak ayarlanır. Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> sınıfının otomatik boyutlandırma buluşsal yöntemleri 'nin kullanıldığı anlamına gelir. Önbellek uygulamasının her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarına göre geçerli bellek yükünü karşılaştırır.  
  
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

- [\<memoryCache > öğesi (önbellek ayarları)](memorycache-element-cache-settings.md)
