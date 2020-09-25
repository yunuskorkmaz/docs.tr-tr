---
title: <memoryCache> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 14480682c5d221216df5da3844897855d1d92a0d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192431"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache> Öğesi (Önbellek Ayarları)

Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> . <xref:System.Runtime.Caching.Configuration.MemoryCacheElement>Sınıfı, önbelleği yapılandırmak için kullanabileceğiniz bir [MemoryCache](memorycache-element-cache-settings.md) öğesi tanımlar. Sınıfın birden çok örneği <xref:System.Runtime.Caching.MemoryCache> tek bir uygulamada kullanılabilir. `memoryCache`Yapılandırma dosyasındaki her öğe, adlandırılmış bir örnek için ayarları içerebilir <xref:System.Runtime.Caching.MemoryCache> .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a>Tür  

 <xref:System.Runtime.Caching.MemoryCache> sınıfı.  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Bir nesne örneğinin büyüyebileceği maksimum bellek boyutu (megabayt cinsinden) <xref:System.Runtime.Caching.MemoryCache> . Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`Name`|Önbellek yapılandırmasının adı.|  
|`PhysicalMemoryLimitPercentage`|Önbellek tarafından kullanılabilen fiziksel bellek yüzdesi. Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın AutoSize buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`PollingInterval`|Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer. Değer "HH: MM: SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Örnek için yapılandırma ayarlarının bir koleksiyonunu içerir `namedCache` .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 <xref:System.Runtime.Caching.MemoryCache>Sınıf, soyut sınıfın somut bir uygulamasıdır <xref:System.Runtime.Caching.ObjectCache> . Sınıf örnekleri, <xref:System.Runtime.Caching.MemoryCache> uygulama yapılandırma dosyalarından yapılandırma bilgileriyle sağlanabilir. [MemoryCache](memorycache-element-cache-settings.md) yapılandırma bölümü bir `namedCaches` yapılandırma koleksiyonu içerir.  
  
 Bellek tabanlı önbellek nesnesi başlatıldığında, önce `namedCaches` bellek önbelleği oluşturucusuna geçirilen parametresindeki adla eşleşen bir giriş bulmaya çalışır. Bir `namedCaches` giriş bulunursa, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.  
  
 Başlatma işlemi daha sonra, kurucudaki yapılandırma bilgileri için isteğe bağlı ad/değer çiftleri koleksiyonu kullanılarak herhangi bir yapılandırma girişinin geçersiz kılınıp kılınmadığını belirler. Ad/değer çifti koleksiyonunda aşağıdaki değerlerden birini geçirirseniz, bu değerler yapılandırma dosyasından elde edilen bilgileri geçersiz kılar:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Runtime.Caching.MemoryCache> `name` özniteliğini "default" olarak ayarlayarak nesnenin adının varsayılan önbellek nesnesi adına nasıl ayarlanacağını gösterir.  
  
 `cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryLimitPercentage` özniteliği sıfır olarak ayarlanır. Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir. Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.  
  
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
- [\<system.runtime.caching> Öğesi (önbellek ayarları)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches> Öğesi (önbellek ayarları)](namedcaches-element-cache-settings.md)
