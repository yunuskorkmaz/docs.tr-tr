---
title: "&lt;defaultFtpCachePolicy&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0c62be73db6d9d0b6ce67dd87021c589502d5fec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a>&lt;defaultFtpCachePolicy&gt; öğesi (ağ ayarları)
FTP önbelleğe alma etkindir ve ilke önbelleğe almayı varsayılan açıklar olup olmadığını açıklar.  
  
 \<Yapılandırma >  
\<System.NET >  
\<requestCaching >  
\<defaultFtpCachePolicy >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`policyLevel`|İlke önbelleği FTP belirtir. Varsayılan değer `Default` şeklindedir.|  
  
## <a name="policylevel-attribute"></a>policyLevel özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`Default`|Önbelleğe alınan kaynak yeni bir kaynaktır, içerik uzunluğu doğru olduğundan ve süre sonu, değiştirilmesi ve içerik uzunluğu öznitelikleri mevcut döndürür.|  
|`BypassCache`|Kaynak sunucudan döndürür.|  
|`CacheOnly`|İçerik uzunluğu varsa ve giriş boyutu eşleşen önbelleğe alınan kaynak döndürür.|  
|`CacheIfAvailable`|İçerik uzunluğu sağlanır ve giriş boyutu eşleşiyorsa önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucudan indirilir ve çağırana döndürülür.|  
|`Revalidate`|Önbelleğe alınan kaynak damgası kaynak sunucuda damgası ile aynı olduğunda önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucudan, önbellekte depolanır ve yapana.|  
|`Reload`|Kaynak sunucudan indirir, önbellekte depolar ve kaynak çağırana döndürür.|  
|`NoCacheNoStore`|Önbelleğe alınan bir kaynak zaten varsa, bu silinir. Kaynak sunucudan indirilir ve çağırana döndürülür.|  
|`Revalidate`|Bir istek zaman damgası kaynak sunucuda damgası ile aynı olduğunda, kaynak önbelleğe alınmış bir kopyasını kullanarak karşılayan; Aksi halde, kaynak sunucudan, çağırana sunulan ve önbellekte depolanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Ağ isteği önbelleğe alma mekanizması denetler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, önbelleğe alma İlkesi, bir FTP belirtmek gösterilmiştir `NoCacheNoStore`.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
