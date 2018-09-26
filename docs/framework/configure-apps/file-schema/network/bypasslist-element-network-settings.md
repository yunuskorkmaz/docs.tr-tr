---
title: '&lt;bypasslist&gt; öğesi (ağ ayarları)'
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
ms.openlocfilehash: 3ca7ba9b0e534b5806570580b207da5314243d8f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109046"
---
# <a name="ltbypasslistgt-element-network-settings"></a>&lt;bypasslist&gt; öğesi (ağ ayarları)
Bir proxy sunucu kullanmaması adresleri açıklayan normal bir ifade kümesi sağlar.  
  
 \<Yapılandırma >  
\<system.net>  
\<defaultProxy >  
\<bypasslist >  
  
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
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|Bir IP adresi veya DNS adı için proxy atlama listesi ekler.|  
|[Temizle](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|Atlama listesi temizler.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|Bir IP adresi veya DNS adı proxy atlama listeden kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Atlama listesi içeren URI'leri açıklayan normal ifadeler, <xref:System.Net.WebRequest> örneklere erişmek doğrudan veya proxy sunucusu üzerinden.  
  
 Bu öğe için normal bir ifade belirtirken dikkatli olmanız gerekir. Normal ifade "[a-z] +\\.contoso\\.com" eşleşme barındıran tüm contoso.com etki alanı, ancak bunu ayrıca contoso.com.cpandl.com etki alanındaki herhangi bir ana bilgisayara eşleşen. Contoso.com etki alanındaki bir konak eşleştirmek için bir yer işareti ("$") kullanın: "[a-z] +\\.contoso\\.com$".  
  
 Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadelerinde](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki adres atlama listesine ekler. İlk contoso.com etki alanındaki tüm sunucular için proxy atlar; İkinci IP adresi ile başlayan tüm sunucuların 192.168 ile proxy atlar.  
  
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
