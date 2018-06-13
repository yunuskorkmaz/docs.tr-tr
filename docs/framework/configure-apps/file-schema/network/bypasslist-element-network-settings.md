---
title: '&lt;olarak ayarlanıyor&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d2076ee5e95ab722fe828ee625392671a6281c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743907"
---
# <a name="ltbypasslistgt-element-network-settings"></a>&lt;olarak ayarlanıyor&gt; öğesi (ağ ayarları)
Bir proxy kullanmayın adresleri açıklamak normal bir ifade kümesi sağlar.  
  
 \<Yapılandırma >  
\<system.net>  
\<defaultProxy >  
\<olarak ayarlanıyor >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|Bir IP adresi veya DNS adı proxy atlama listesine ekler.|  
|[Temizle](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|Atlama listesi temizler.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|Bir IP adresi veya DNS adı proxy atlama listesinden kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 URI'ler açıklamak normal ifadeler atlama listesi içerir, <xref:System.Net.WebRequest> örneklere erişmek doğrudan yerine, proxy sunucu üzerinden.  
  
 Bu öğe için normal bir ifade belirtirken dikkatli olmanız gerekir. Normal ifade "[a-z] +\\.contoso\\.com" barındıran tüm contoso.com etki alanı, ancak bunu eşleşmeleri ayrıca contoso.com.cpandl.com etki alanındaki herhangi bir ana eşleşir. Yalnızca bir ana bilgisayar contoso.com etki alanındaki eşleştirmek için bir yer işareti ("$") kullanın: "[a-z] +\\.contoso\\.com$".  
  
 Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadeleri](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki adres atlama listesine ekler. İlk contoso.com etki alanındaki tüm sunucular için proxy atlar; İkinci 192.168 tüm sunucularıyla olan IP adresleri başlamak için proxy atlar.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
