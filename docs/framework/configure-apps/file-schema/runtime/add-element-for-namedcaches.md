---
title: <namedCaches> için <add> öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154511"
---
# <a name="add-element-for-namedcaches"></a>\<adCaches \<> için> Öğesi ekleyin
Bellek `namedCache` önbelleği `namedCaches` için koleksiyona bir giriş ekler.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.önbelleğe alma>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryÖnbellek>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<namedCaches>  
    <add name="Default" />  
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
|`CacheMemoryLimitMegabytes`|İzin verilen en büyük boyutu (megabaytlarda) belirten bir <xref:System.Runtime.Caching.MemoryCache> tamsayı değeri. Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma sezgiselinin varsayılan olarak kullanıldığı anlamına gelir.|  
|`Name`|Önbelleğin adı.|  
|`PhysicalMemoryLimitPercentage`|Önbellek tarafından tüketilebilen fiziksel olarak yüklenmiş bilgisayar belleğinin maksimum yüzdesini belirten 0 ile 100 arasında bir tamsayı değeri. Varsayılan değer 0'dır, bu <xref:System.Runtime.Caching.MemoryCache> da sınıfın otomatik boyutlandırma sezgiselinin varsayılan olarak kullanıldığı anlamına gelir.|  
|`PollingInterval`|Önbellek uygulamasının geçerli bellek yükünü önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarıyla karşılaştırdığı zaman aralığını gösteren bir değer. Bu değer "HH:MM:SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 `None`  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarları koleksiyonu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `add` bellek önbelleği için `namedCaches` koleksiyona bir giriş ekler. Koleksiyonda başka [clear](clear-element-for-namedcaches.md) adlandırılmış önbellek `add` olmadığından emin olmak için öğeyi kullanmadan önce açık öğeyi kullanabilirsiniz. Bu öğe machine.config dosyasında ve Web.config dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir bellek önbelleği `namedCaches` için koleksiyona varsayılan `namedCache` giriş ayarlarının nasıl tanımlanacağını gösterir.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<namedCaches> Öğesi (Önbellek Ayarları)](namedcaches-element-cache-settings.md)
