---
title: <defaultProxy> Öğesi (Ağ Ayarları)
description: <defaultProxy>Ağ ayarları öğesi .NET Framework Köprü Metni Aktarım Protokolü (http) proxy sunucusunu yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 915fdc96dbd4d417f9c9e6aa3ff96de3026491ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504608"
---
# <a name="defaultproxy-element-network-settings"></a>\<defaultProxy> Öğesi (Ağ Ayarları)
Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|Bir Web proxy 'sinin kullanılıp kullanılmayacağını belirtir. Varsayılan değer: `true`.|  
|`useDefaultCredentials`|Bu konak için varsayılan kimlik bilgilerinin Web proxy 'sine erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer: `false`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[BypassList](bypasslist-element-network-settings.md)|Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.|  
|[birimi](module-element-network-settings.md)|Uygulamaya yeni bir proxy modülü ekler.|  
|[proxy](proxy-element-network-settings.md)|Bir ara sunucu tanımlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 DefaultProxy öğesi boşsa, Internet Explorer 'daki proxy ayarları kullanılacaktır. Bu davranış .NET Framework 1,1 sürümünden farklıdır.  
  
 [Modül](module-element-network-settings.md) öğesi ortak olmayan bir tür belirtiyorsa, tür sınıftan türetilmiyor <xref:System.Net.IWebProxy> , bu nesnenin parametresiz oluşturucusundan bir özel durum oluştu veya sistem tarafından belirtilen varsayılan proxy alınırken özel durum oluştu. <xref:System.Exception.InnerException%2A>Özel durum üzerindeki özelliği, hatanın kök nedeni hakkında daha fazla bilgi içermelidir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Internet Explorer proxy 'sinden varsayılan değerleri kullanır, proxy adresini belirtir ve yerel erişim ve contoso.com için proxy 'yi atlar.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
