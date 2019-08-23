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
ms.openlocfilehash: bd746f07b4c4eb08bf34b01d555b5799d9af0cf3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927470"
---
# <a name="bypasslist-element-network-settings"></a>\<BypassList > öğesi (ağ ayarları)
Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.  
  
 \<Yapılandırma >  
\<system.net>  
\<defaultProxy >  
\<BypassList >  
  
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
|[add](add-element-for-bypasslist-network-settings.md)|Proxy atlama listesine bir IP adresi veya DNS adı ekler.|  
|[lediğiniz](clear-element-for-bypasslist-network-settings.md)|Atlama listesini temizler.|  
|[remove](remove-element-for-bypasslist-network-settings.md)|Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Atlama listesi, proxy sunucu aracılığıyla değil, doğrudan erişim <xref:System.Net.WebRequest> sağlayan URI 'leri tanımlayan normal ifadeler içerir.  
  
 Bu öğe için bir normal ifade belirtirken dikkatli olmanız gerekir. "[A-z] +\\. contoso\\. com" normal ifadesi, contoso.com etki alanındaki herhangi bir konakla eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanındaki herhangi bir konakla eşleşir. Yalnızca contoso.com etki alanındaki bir konağı eşleştirmek için bir tutturucu ("$"): "[a-z] +\\. contoso\\. com $" kullanın.  
  
 Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
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
- [Ağ Ayarları Şeması](index.md)
