---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 46f430f7cf112da40aa3b25bfb280c5014612eae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663613"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache > öğesi (önbellek ayarları)
<xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar. Sınıfı, önbelleği yapılandırmak için kullanabileceğiniz bir memoryCache öğesi tanımlar. [](memorycache-element-cache-settings.md) <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> <xref:System.Runtime.Caching.MemoryCache> Sınıfın birden çok örneği tek bir uygulamada kullanılabilir. Yapılandırma `memoryCache` dosyasındaki her öğe, adlandırılmış <xref:System.Runtime.Caching.MemoryCache> bir örnek için ayarları içerebilir.  
  
 \<Yapılandırma >  
\<System. Runtime. Caching >  
\<memoryCache >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a>Tür  
 <xref:System.Runtime.Caching.MemoryCache>sınıfı.  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Bir <xref:System.Runtime.Caching.MemoryCache> nesne örneğinin büyüyebileceği maksimum bellek boyutu (megabayt cinsinden). Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`Name`|Önbellek yapılandırmasının adı.|  
|`PhysicalMemoryLimitPercentage`|Önbellek tarafından kullanılabilen fiziksel bellek yüzdesi. Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`PollingInterval`|Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer. Değer "HH: MM: SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Namedönbellekler >](namedcaches-element-cache-settings.md)|`namedCache` Örnek için yapılandırma ayarlarının bir koleksiyonunu içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System. Runtime. Caching >](system-runtime-caching-element-cache-settings.md)|.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf, soyut <xref:System.Runtime.Caching.ObjectCache> sınıfın somut bir uygulamasıdır. <xref:System.Runtime.Caching.MemoryCache> Sınıf örnekleri, <xref:System.Runtime.Caching.MemoryCache> uygulama yapılandırma dosyalarından yapılandırma bilgileriyle sağlanabilir. [MemoryCache](memorycache-element-cache-settings.md) yapılandırma bölümü bir `namedCaches` yapılandırma koleksiyonu içerir.  
  
 Bellek tabanlı önbellek nesnesi başlatıldığında, önce bellek önbelleği oluşturucusuna geçirilen parametresindeki adla eşleşen bir `namedCaches` giriş bulmaya çalışır. Bir `namedCaches` giriş bulunursa, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.  
  
 Başlatma işlemi daha sonra, kurucudaki yapılandırma bilgileri için isteğe bağlı ad/değer çiftleri koleksiyonu kullanılarak herhangi bir yapılandırma girişinin geçersiz kılınıp kılınmadığını belirler. Ad/değer çifti koleksiyonunda aşağıdaki değerlerden birini geçirirseniz, bu değerler yapılandırma dosyasından elde edilen bilgileri geçersiz kılar:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> `name` özniteliğini "default" olarak ayarlayarak nesnenin adının varsayılan önbellek nesnesi adına nasıl ayarlanacağını gösterir.  
  
 `cacheMemoryLimitMegabytes` Özniteliği`physicalMemoryLimitPercentage` ve özniteliği sıfır olarak ayarlanır. Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir. Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.  
  
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
- [\<System. Runtime. Caching > öğesi (önbellek ayarları)](system-runtime-caching-element-cache-settings.md)
- [\<Namedönbellekler > öğesi (önbellek ayarları)](namedcaches-element-cache-settings.md)
