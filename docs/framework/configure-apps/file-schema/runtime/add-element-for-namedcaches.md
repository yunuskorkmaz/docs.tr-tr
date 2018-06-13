---
title: '&lt;ekleme&gt; öğesi için &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743829"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a>&lt;ekleme&gt; öğesi için &lt;namedCaches&gt;
Ekler bir `namedCache` girişe `namedCaches` bir önbellek için koleksiyonu.  
  
 \<System.Runtime.Caching >  
\<memoryCache >  
\<namedCaches >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Tür  
 `None`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|-|-|  
|`CacheMemoryLimitMegabytes`|(Megabayt cinsinden) izin verilen maksimum boyut belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> için büyüyebilir. Varsayılan değer anlamına 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`Name`|Önbellek adı.|  
|`PhysicalMemoryLimitPercentage`|Önbellek tarafından kullanılabilecek yüklü olan fiziksel bilgisayar belleğini yüzdesinin üst sınırını belirtir 0 ile 100 arasında bir tamsayı değeri. Varsayılan değer anlamına 0'dır <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`PollingInterval`|Daha sonra önbellek uygulaması için önbellek örneğini ayarlamak mutlak ve yüzde tabanlı bellek sınırları göre geçerli bellek yükü karşılaştırır zaman aralığını gösteren bir değer. Bu değer "Ss: dd:" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 `None`  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches >](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Yapılandırma ayarları adlandırılmış bir koleksiyonu içerir <xref:System.Runtime.Caching.MemoryCache> örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `add` Öğesi ekler bir girişe `namedCaches` bir önbellek için koleksiyonu. Kullanabileceğiniz [temizleyin](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) kullanmadan önce öğesi `add` olduğunu başka emin olmak için öğe koleksiyonda önbellekleri adlı. Bu öğe machine.config dosyasındaki ve Web.config dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan ayarları belirlemek gösterilmiştir `namedCache` girişe `namedCaches` bir önbellek için koleksiyonu.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<namedCaches > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
