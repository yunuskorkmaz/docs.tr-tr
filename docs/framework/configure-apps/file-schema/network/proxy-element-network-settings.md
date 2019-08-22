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
ms.openlocfilehash: a183c4160c4cd55b05c5c23f7a10e3a1d1c74ea4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659284"
---
# <a name="proxy-element-network-settings"></a>\<Proxy > öğesi (ağ ayarları)
Bir ara sunucu tanımlar.  
  
 \<Yapılandırma >  
\<system.net>  
\<defaultProxy >  
\<Proxy >  
  
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
|`autoDetect`|Proxy 'nin otomatik olarak algılanıp algılanmayacağını belirtir. Varsayılan değer `unspecified` şeklindedir.|  
|`bypassonlocal`|Yerel kaynaklar için proxy 'nin atlanıp atlanmayacağını belirtir. Yerel sunucu (`http://localhost`, `http://loopback`, veya `http://127.0.0.1`) ve nokta (`http://webserver`) olmayan bir URI 'yi içerir. Varsayılan değer `unspecified` şeklindedir.|  
|`proxyaddress`|Kullanılacak proxy URI 'sini belirtir.|  
|`scriptLocation`|Yapılandırma betiğinin konumunu belirtir. Bu öznitelikle `bypassonlocal` özniteliğini kullanmayın. |  
|`usesystemdefault`|Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir. Olarak `true`ayarlanırsa, sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar. Varsayılan değer `unspecified` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="text-value"></a>Metin Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesi `proxy` , bir uygulama için ara sunucu tanımlar. Yapılandırma dosyasında bu öğe eksikse .NET Framework, Internet Explorer 'daki proxy ayarlarını kullanacaktır.  
  
 `proxyaddress` Özniteliğin değeri iyi biçimlendirilmiş bir Tekdüzen Kaynak göstergesi (URI) olmalıdır.  
  
 `scriptLocation` Öznitelik, proxy yapılandırma betikleri otomatik olarak algılanmasını ifade eder. Bu sınıf, Internet Explorer 'da **otomatik yapılandırma betiği kullan** seçeneği belirlendiğinde bir yapılandırma betiğini (genellikle WPAD. dat olarak adlandırılır) bulmaya çalışır. <xref:System.Net.WebProxy> Herhangi bir değere ayarlanırsa, `scriptLocation` yok sayılır. `bypassonlocal`
  
 2,0 sürümüne geçiş yapan .NET Framework sürüm 1,1 uygulamaları için özniteliğinikullanın.`usesystemdefault`  
  
 `proxyaddress` Öznitelik geçersiz bir varsayılan proxy belirtiyorsa bir özel durum oluşur. Özel durum üzerindeki özelliği, hatanın kök nedeni hakkında daha fazla bilgi içermelidir. <xref:System.Exception.InnerException%2A>  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Internet Explorer proxy 'sinin varsayılan değerlerini kullanır, proxy adresini belirtir ve yerel erişim için ara sunucuyu atlar.  
  
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
