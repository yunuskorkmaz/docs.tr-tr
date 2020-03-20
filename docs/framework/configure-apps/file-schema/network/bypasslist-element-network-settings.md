---
title: <bypasslist> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154952"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> Öğesi (Ağ Ayarları)
Proxy kullanmayan adresleri açıklayan bir dizi düzenli ifade sağlar.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

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
|[Ekle](add-element-for-bypasslist-network-settings.md)|Proxy bypass listesine bir IP adresi veya DNS adı ekler.|  
|[Temizleyin](clear-element-for-bypasslist-network-settings.md)|Bypass listesini temizler.|  
|[Kaldırmak](remove-element-for-bypasslist-network-settings.md)|Proxy bypass listesinden bir IP adresi veya DNS adını kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Baypas listesi, proxy sunucusu yerine doğrudan <xref:System.Net.WebRequest> erişim örnekleri uris açıklayan düzenli ifadeler içerir.  
  
 Bu öğe için düzenli bir ifade belirtirken dikkatli olmalısınız. Normal ifade "[a-z]+\\.contoso\\.com" contoso.com etki alanında herhangi bir ana bilgisayar eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanında herhangi bir ana bilgisayar eşleşir. Yalnızca contoso.com etki alanında bir ana bilgisayarla eşleştirmek için bir bağlantı ("$"): "[a-z]+\\.contoso\\.com$" kullanın.  
  
 Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET Framework Düzenli İfadeler](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, baypas listesine iki adres ekler. İlki, contoso.com etki alanında bulunan tüm sunucular için proxy'yi atlar; ikincisi, IP adresleri 192.168 ile başlayan tüm sunucular için proxy'yi atlar.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
