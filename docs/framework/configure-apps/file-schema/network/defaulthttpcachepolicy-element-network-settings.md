---
title: <defaultHttpCachePolicy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: c5029a7d1e53c28d0abb232efdc3e0bd2c9658d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088414"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a>\<defaultHttpCachePolicy > öğesi (ağ ayarları)
HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultHttpCachePolicy >**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maximumAge`|Önbelleğe alınan bir nesnenin süresi dolmadan önce geçen maksimum zaman aralığını belirtir.|  
|`maximumStale`|Önbelleğe alınmış bir nesne, süresi dolmadan önce, hesaplanan yeniliği geçen en uzun süreyi belirtir.|  
|`minimumFresh`|Önbelleğe alınmış bir nesnenin yeni olarak kabul edileceği en kısa süreyi belirtir.|  
|`policyLevel`|Önbelleğe alma ilkesinin otomatik olup olmadığını veya önbelleğin atlanıp atlanmayacağını belirtir. Varsayılan değer `BypassCache` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizmasını denetler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `policyLevel` özniteliğinin değeri `BypassCache` veya `Default`.  
  
 `maximumAge`, `maximumStale`ve `minimumFresh` öğelerinin değerleri, *d*biçimindeki açık bir zaman aralığıdır. *SS*:*dd*:*SS* (gün, saat, dakika, saniye) veya `minValue` ya da `maxValue`sabitler uygun şekilde.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, en az altı saat, iki güne ait maksimum yaş süresi ve dört saatlik en fazla eski süreyi belirtmek için nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Ağ Ayarları Şeması](index.md)
