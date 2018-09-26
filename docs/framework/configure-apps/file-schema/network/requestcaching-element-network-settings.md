---
title: '&lt;requestCaching&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3e014c7a47a53a424bbaef51c9acb28e59b43078
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083195"
---
# <a name="ltrequestcachinggt-element-network-settings"></a>&lt;requestCaching&gt; öğesi (ağ ayarları)
Ağ istekleri için önbelleğe alma mekanizması denetler.  
  
 \<Yapılandırma >  
\<system.net>  
\<requestCaching >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`isPrivateCache`|Önbellek bilgilerinin farklı kullanıcılar arasında yalıtım sağlayıp sağlamadığını belirtir. Varsayılan değer `true` şeklindedir. Bu değer olmalıdır `false` orta katman uygulamaları için.|  
|`disableAllCaching`|Önbelleğe alma için tüm Web yanıtları devre dışı bırakıldı ve programlı olarak geçersiz kılınamaz belirtir.|  
|`defaultPolicyLevel`|Değerlerin birini <xref:System.Net.Cache.RequestCacheLevel> sabit listesi. Varsayılan değer `BypassCache` şeklindedir.|  
|`unspecifiedMaximumAge`|Sonra içeriğin süresi dolmuş olarak işaretlenmiş varsayılan süreyi belirtir.|  
  
## <a name="policylevel-attribute"></a>policyLevel özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`Default`|Önbelleğe alınmış kaynak sona erme, değiştirilmesi ve içerik uzunluğu öznitelikleri mevcut olduğundan yeni bir kaynaktır ve içerik uzunluğu doğru döndürür.|  
|`BypassCache`|Kaynak sunucudan döndürür.|  
|`CacheOnly`|İçerik uzunluğu varsa ve giriş boyutu eşleşen önbelleğe alınmış kaynak döndürür.|  
|`CacheIfAvailable`|İçerik uzunluğu sağlanır ve giriş boyutu eşleşiyorsa, önbelleğe alınmış kaynak döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.|  
|`Revalidate`|Önbelleğe alınmış kaynak zaman damgası önbelleğe alınmış kaynak sunucusunda kaynak zaman damgası ile aynı olduğunda döndürür; Aksi takdirde, kaynak sunucudan önbelleğinde depolanan indirilir ve çağırana döndürülür.|  
|`Reload`|Kaynak sunucudan indirir, önbellekte depolar ve kaynak çağırana döner.|  
|`NoCacheNoStore`|Önbelleğe alınan bir kaynağın varolup olmadığını silinir. Kaynak sunucudan indirilir ve çağırana döndürülür.|  
|`Revalidate`|Bir istek, zaman damgası zaman damgasını kaynak sunucudaki aynı olduğunda, kaynağın önbelleğe alınmış kopyasını kullanarak karşılayan; Aksi takdirde, kaynak sunucudan arayana sunulan yüklenir ve önbellekte depolanır,|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|İsteğe bağlı öğe.<br /><br /> HTTP önbelleğe alma etkindir ve önbelleğe alma ilkesi varsayılan tanımlar olup olmadığını açıklar.|  
|[\<defaultFtpCachePolicy > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|İsteğe bağlı öğe.<br /><br /> FTP önbelleğe alma etkindir ve önbelleğe alma ilkesi varsayılan tanımlar olup olmadığını açıklar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm önbelleğe alma işlemlerini devre dışı bırakmak gösterilmektedir.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
