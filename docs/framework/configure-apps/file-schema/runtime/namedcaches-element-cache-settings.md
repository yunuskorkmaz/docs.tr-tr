---
title: <namedCaches> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: ad76c01bba859934be399d73262bd974309efe98
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192405"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches> Öğesi (Önbellek Ayarları)

Adlandırılmış örnekler için yapılandırma ayarları koleksiyonunu belirtir <xref:System.Runtime.Caching.MemoryCache> . <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Özelliği yapılandırma dosyasının bir veya daha fazla öğesinden yapılandırma ayarları koleksiyonuna başvurur `namedCaches` .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`cacheMemoryLimitMegabytes`|Bir örneğinin bir örneğinin büyüyebileceği en fazla izin verilen boyutu megabayt cinsinden belirten bir tamsayı değeri <xref:System.Runtime.Caching.MemoryCache> . Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.|  
|`name`|Önbelleğin adı.|  
|`physicalMemoryLimitPercentage`|0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri. Varsayılan değer 0 ' dır. Bu, sınıfının otomatik boyutlandırma buluşsal yöntemleri <xref:System.Runtime.Caching.MemoryCache> Varsayılan olarak kullanıldığı anlamına gelir.|  
|`pollingInterval`|Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer. Bu değer "HH: MM: SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|`namedCaches`Bir bellek önbelleği için koleksiyona adlandırılmış bir önbellek ekler.|  
|[\<clear>](clear-element-for-namedcaches.md)|`namedCaches`Bir bellek önbelleğinin koleksiyonunu temizler.|  
|[\<remove>](remove-element-for-namedcaches.md)|`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|.NET Framework yerleşik uygulamalarda çıktı önbelleği uygulamanıza olanak sağlayan türler içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Web.config dosyanın bellek önbelleği yapılandırması bölümü `add` `remove` `clear` koleksiyon için, ve özniteliklerini içerebilir `namedCaches` . Her `namedCaches` giriş, öznitelik tarafından benzersiz şekilde tanımlanır `name` .  
  
 Uygulama yapılandırma dosyalarındaki bilgilere başvurarak bellek önbelleği girdilerinin örneklerini alabilirsiniz. Varsayılan olarak, yalnızca varsayılan önbellek örneğinin yapılandırma dosyasında bir girişi vardır. Varsayılan önbellek örneği özelliğinden döndürülen örneğidir <xref:System.Runtime.Caching.MemoryCache.Default%2A> .  
  
 Name özniteliğini "default" olarak ayarlarsanız, öğesi varsayılan bellek önbelleği örneğini kullanır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `name` özniteliğini "default" olarak ayarlayarak önbelleğin adının varsayılan önbellek girişi adına nasıl ayarlanacağını gösterir.  
  
 `cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır. Bu özniteliklerin sıfıra ayarlanması, sınıfının otomatik boyutlandırma buluşsal yöntemleri 'nin kullanıldığı anlamına gelir <xref:System.Runtime.Caching.MemoryCache> . Önbellek uygulamasının her iki dakikada bir mutlak ve yüzde tabanlı bellek sınırlarına göre geçerli bellek yükünü karşılaştırır.  
  
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

- [\<memoryCache> Öğesi (önbellek ayarları)](memorycache-element-cache-settings.md)
