---
title: <proxy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154796"
---
# <a name="proxy-element-network-settings"></a>\<proxy> Elemanı (Ağ Ayarları)
Proxy sunucusu tanımlar.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`autoDetect`|Proxy'nin otomatik olarak algılanıp algılanmayanı belirtir. Varsayılan değer: `unspecified`.|  
|`bypassonlocal`|Proxy'nin yerel kaynaklar için atlanıp atlanıp atlılmayacağını belirtir. Yerel kaynaklar yerel sunucu`http://localhost` `http://loopback`(, `http://127.0.0.1`, veya ) ve`http://webserver`bir dönem olmadan bir URI içerir ( ). Varsayılan değer: `unspecified`.|  
|`proxyaddress`|Kullanılacak proxy URI'yi belirtir.|  
|`scriptLocation`|Yapılandırma komut dosyasının konumunu belirtir. Özniteliği bu `bypassonlocal` öznitelik ile kullanmayın. |  
|`usesystemdefault`|Internet Explorer proxy ayarlarını kullanıp kullanmayacağını belirtir. `true`Ayarlanırsa, sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar. Varsayılan değer: `unspecified`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="text-value"></a>Metin Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `proxy` bir uygulama için bir proxy sunucusu tanımlar. Bu öğe yapılandırma dosyasında eksikse, .NET Framework Internet Explorer'daki proxy ayarlarını kullanır.  
  
 Öznitelik değeri `proxyaddress` iyi biçimlendirilmiş bir Tekdüzen Kaynak Göstergesi (URI) olmalıdır.  
  
 Öznitelik `scriptLocation` proxy yapılandırma komut dosyalarının otomatik algılama anlamına gelir. Sınıf, <xref:System.Net.WebProxy> Internet Explorer'da **Otomatik yapılandırma komut dosyası kullan** seçeneği seçildiğinde bir yapılandırma komut dosyası (genellikle Wpad.dat olarak adlandırılır) bulmaya çalışır. Herhangi `bypassonlocal` bir değere `scriptLocation` ayarlanmışsa, yoksayılır.
  
 `usesystemdefault` .NET Framework sürüm 1.1 uygulamalarının sürüm 2.0'a geçiş yapan özniteliğini kullanın.  
  
 `proxyaddress` Öznitelik geçersiz bir varsayılan proxy belirtirse bir özel durum atılır. Özel <xref:System.Exception.InnerException%2A> durum özelliği, hatanın temel nedeni hakkında daha fazla bilgiye sahip olmalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Internet Explorer proxy'sinden varsayılanları kullanır, proxy adresini belirtir ve yerel erişim için proxy'yi atlar.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
