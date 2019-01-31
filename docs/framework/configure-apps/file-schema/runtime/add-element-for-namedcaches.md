---
title: <add> için <namedCaches> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: cbe7c98e9603e51aa381f07ea35ffe46e6d3adfb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257368"
---
# <a name="add-element-for-namedcaches"></a>\<Ekle > öğesi için \<namedCaches >
Ekler bir `namedCache` girişe `namedCaches` koleksiyonu için bir önbellek.  
  
 \<System.Runtime.Caching >  
\<memoryCache>  
\<namedCaches>  
\<Ekle >  
  
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
|`CacheMemoryLimitMegabytes`|(Megabayt olarak) boyutu izin verilen maksimum belirten bir tamsayı değeri, örneği bir <xref:System.Runtime.Caching.MemoryCache> kadar büyüyebilir. Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`Name`|Önbellek adı.|  
|`PhysicalMemoryLimitPercentage`|Önbelleği tarafından tüketilebilecek yüklü olan fiziksel bilgisayar belleğini en yüksek yüzdesi belirten bir tamsayı değeri 0 ile 100 arasında. Varsayılan değerdir, yani 0 <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemler, varsayılan olarak kullanılır.|  
|`PollingInterval`|Daha sonra önbellek uygulaması geçerli bellek yükü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarını karşı karşılaştırır zaman aralığını belirten bir değer. Bu değer, "Ss" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 `None`  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Yapılandırma ayarları için adlandırılmış bir koleksiyonunu içeren <xref:System.Runtime.Caching.MemoryCache> örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `add` Öğe için bir giriş ekler `namedCaches` koleksiyonu için bir önbellek. Kullanabileceğiniz [Temizle](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) kullanmadan önce öğesi `add` olduğunu başka hiçbir emin olmak için öğesi adlı önbellekler koleksiyondaki. Bu öğe, machine.config dosyasında ve Web.config dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan ayarları belirlemek gösterilmektedir `namedCache` girişe `namedCaches` koleksiyonu için bir önbellek.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [\<namedCaches > öğesi (önbellek ayarları)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
