---
title: <namedCaches> için <add> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659028"
---
# <a name="add-element-for-namedcaches"></a>\<namedönbellekler için \<> öğesi ekleyin >
Bir bellek `namedCache` önbelleği için `namedCaches` koleksiyona bir giriş ekler.  
  
 \<System. Runtime. Caching >  
\<memoryCache >  
\<Namedönbellekler >  
\<> Ekle  
  
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
|`CacheMemoryLimitMegabytes`|Bir örneğinin bir <xref:System.Runtime.Caching.MemoryCache> örneğinin büyüyebileceği en fazla izin verilen boyutu (megabayt cinsinden) belirten bir tamsayı değeri. Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`Name`|Önbelleğin adı.|  
|`PhysicalMemoryLimitPercentage`|0 ile 100 arasında, önbellek tarafından tüketilen fiziksel olarak yüklenen bilgisayar belleğinin maksimum yüzdesini belirten bir tamsayı değeri. Varsayılan değer 0 ' dır. Bu, <xref:System.Runtime.Caching.MemoryCache> sınıfın otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir.|  
|`PollingInterval`|Önbellek uygulamasının geçerli bellek yükünü, önbellek örneği için ayarlanan mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştıran zaman aralığını belirten bir değer. Bu değer "HH: MM: SS" biçiminde girilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 `None`  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Namedönbellekler >](namedcaches-element-cache-settings.md)|Adlandırılmış <xref:System.Runtime.Caching.MemoryCache> örnekler için yapılandırma ayarlarının bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesi `add` , bir bellek önbelleği için `namedCaches` koleksiyona bir giriş ekler. Koleksiyonda başka bir adlandırılmış [](clear-element-for-namedcaches.md) önbellek bulunmadığından emin olmak için `add` öğesini kullanmadan önce Clear öğesini kullanabilirsiniz. Bu öğe Machine. config dosyasında ve Web. config dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir bellek önbelleğinin `namedCache` `namedCaches` koleksiyonuna varsayılan giriş için ayarların nasıl tanımlanacağını gösterir.  
  
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

- [\<Namedönbellekler > öğesi (önbellek ayarları)](namedcaches-element-cache-settings.md)
