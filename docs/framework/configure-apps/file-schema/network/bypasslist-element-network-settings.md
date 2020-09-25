---
title: <bypasslist> Öğesi (Ağ Ayarları)
description: <bypasslist>Ağ ayarları öğesi, .NET Framework proxy kullanmayan adresleri tanımlayan bir dizi normal ifade sağlar.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 58cdcf046b2a5a292493c5704739b22aa4ec4f17
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178417"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> Öğesi (Ağ Ayarları)

Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a>Syntax  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[add](add-element-for-bypasslist-network-settings.md)|Proxy atlama listesine bir IP adresi veya DNS adı ekler.|  
|[lediğiniz](clear-element-for-bypasslist-network-settings.md)|Atlama listesini temizler.|  
|[temizlenmesine](remove-element-for-bypasslist-network-settings.md)|Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Atlama listesi, <xref:System.Net.WebRequest> proxy sunucu aracılığıyla değil, doğrudan erişim sağlayan URI 'leri tanımlayan normal ifadeler içerir.  
  
 Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir. "[A-z] + \\ . contoso \\ . com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir. Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] + \\ . contoso \\ . com $" kullanın.  
  
 Normal ifadeler hakkında daha fazla bilgi için bkz.. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek atlama listesine iki adres ekler. İlki, contoso.com etki alanındaki tüm sunucular için proxy 'yi atlar; İkincisi, IP adresleri 192,168 ile başlayan tüm sunucular için proxy 'yi atlar.  
  
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
- [Ağ ayarları şeması](index.md)
