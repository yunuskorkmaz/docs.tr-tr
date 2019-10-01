---
title: <defaultProxy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 0945629c1395917bc1cf825f2ba84d20afa99957
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698202"
---
# <a name="defaultproxy-element-network-settings"></a>\<defaultProxy > öğesi (ağ ayarları)
Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<defaultProxy >**  
  
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
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|Bir Web proxy 'sinin kullanılıp kullanılmayacağını belirtir. Varsayılan değer `true` şeklindedir.|  
|`useDefaultCredentials`|Bu konak için varsayılan kimlik bilgilerinin Web proxy 'sine erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[BypassList](bypasslist-element-network-settings.md)|Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.|  
|[module](module-element-network-settings.md)|Uygulamaya yeni bir proxy modülü ekler.|  
|[Proxy](proxy-element-network-settings.md)|Bir ara sunucu tanımlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 DefaultProxy öğesi boşsa, Internet Explorer 'daki proxy ayarları kullanılacaktır. Bu davranış .NET Framework 1,1 sürümünden farklıdır.  
  
 [Modül](module-element-network-settings.md) öğesi ortak olmayan bir tür belirtiyorsa bir özel durum oluşur, tür <xref:System.Net.IWebProxy> sınıfından türetilmez, bu nesnenin parametresiz oluşturucusundan bir özel durum oluştu veya bir özel durum alınırken hata oluştu sistem tarafından belirtilen varsayılan proxy. Özel durumun <xref:System.Exception.InnerException%2A> özelliği, hatanın kök nedeni hakkında daha fazla bilgi içermelidir.  
  
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
