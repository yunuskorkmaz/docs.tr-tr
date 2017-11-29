---
title: "&lt;memoryCache&gt; öğesi (önbellek ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ded74486fd9a5687a9f5cdeee6061d4d58234e37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmemorycachegt-element-cache-settings"></a>&lt;memoryCache&gt; öğesi (önbellek ayarları)
Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı. <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Sınıfı tanımlayan bir [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) önbelleğini yapılandırmak için kullanabileceğiniz öğesi. Birden çok örneğini <xref:System.Runtime.Caching.MemoryCache> sınıfı tek bir uygulamada kullanılabilir. Her `memoryCache` öğesi yapılandırma dosyasında bir adlandırılmış için ayarları içerebilir <xref:System.Runtime.Caching.MemoryCache> örneği.  
  
 \<Yapılandırma >  
\<System.Runtime.Caching >  
\<memoryCache >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<memoryCache   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
< memoryCache />  
```  
  
## <a name="type"></a>Tür  
 <xref:System.Runtime.Caching.MemoryCache>sınıf.  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Megabayt cinsinden en büyük bellek boyutu, örneği bir <xref:System.Runtime.Caching.MemoryCache> nesne büyüme için. Varsayılan değer anlamına 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfının autosize buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`Name`|Önbellek yapılandırmasının adı.|  
|`PhysicalMemoryLimitPercentage`|Önbellek tarafından kullanılan fiziksel bellek yüzdesi. Varsayılan değer anlamına 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfının autosize buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`PollingInterval`|Daha sonra önbellek uygulaması için önbellek örneğini ayarlamak mutlak ve yüzde tabanlı bellek sınırları göre geçerli bellek yükü karşılaştırır zaman aralığını gösteren bir değer. Değer "Ss: dd:" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches >](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Bir koleksiyon için yapılandırma ayarlarını içeren `namedCache` örneği.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.Runtime.Caching >](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Çıktı önbelleği içinde yerleşik olarak bulunan uygulamalarda uygulamanıza olanak sağlayan türleri içerir [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Runtime.Caching.MemoryCache> Sınıftır abstract somut uyarlamasını <xref:System.Runtime.Caching.ObjectCache> sınıfı. Örneklerini <xref:System.Runtime.Caching.MemoryCache> sınıfı sağlanan uygulama yapılandırma dosyaları yapılandırma bilgileriyle. [MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) yapılandırma bölümünü içeren bir `namedCaches` yapılandırma koleksiyonu.  
  
 Bellek tabanlı önbellek nesnesini başlatıldığında, ilk bulmaya çalışır bir `namedCaches` bellek önbelleği oluşturucuya geçirilen parametre adı ile eşleşen girişi. Varsa bir `namedCaches` girişi bulunursa, yoklama ve bellek yönetimi bilgileri yapılandırma dosyasından alınır.  
  
 Başlatma işlemi daha sonra herhangi bir yapılandırma giriş, oluşturucuda isteğe bağlı yapılandırma bilgilerinin ad/değer çiftleri koleksiyonu kullanarak geçersiz olup olmadığını belirler. Aşağıdaki değerlerden birini ad/değer çifti koleksiyonu geçirirseniz, bu değerler yapılandırma dosyasından alınan bilgileri geçersiz kıl:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adını ayarlamak gösterilmiştir <xref:System.Runtime.Caching.MemoryCache> ayarlayarak varsayılan önbellek nesnesi adı nesnesine `name` "varsayılan" özniteliği.  
  
 `cacheMemoryLimitMegabytes` Özniteliği ve `physicalMemoryLimitPercentage` özniteliği sıfır olarak ayarlanır. Bu öznitelikler sıfır olarak ayarlandığında <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır. Önbellek uygulaması mutlak ve yüzde tabanlı bellek sınırları her iki dakikada göre geçerli bellek yükü karşılaştırmanız gerekir.  
  
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
 <xref:System.Runtime.Caching.MemoryCache>  
 [\<System.Runtime.Caching > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
 [\<namedCaches > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
