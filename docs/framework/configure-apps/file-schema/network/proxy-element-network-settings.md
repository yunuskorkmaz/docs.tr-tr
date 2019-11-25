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
ms.openlocfilehash: 5f327a2bb4fe316497614f14669907d514c20654
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089188"
---
# <a name="proxy-element-network-settings"></a>\<proxy > öğesi (ağ ayarları)
Bir ara sunucu tanımlar.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<proxy >**

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
|`bypassonlocal`|Yerel kaynaklar için proxy 'nin atlanıp atlanmayacağını belirtir. Yerel kaynaklar yerel sunucuyu (`http://localhost`, `http://loopback` veya `http://127.0.0.1`) ve nokta olmayan bir URI 'yi (`http://webserver`) içerir. Varsayılan değer `unspecified` şeklindedir.|  
|`proxyaddress`|Kullanılacak proxy URI 'sini belirtir.|  
|`scriptLocation`|Yapılandırma betiğinin konumunu belirtir. Bu öznitelikle `bypassonlocal` özniteliğini kullanmayın. |  
|`usesystemdefault`|Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir. `true`olarak ayarlanırsa, sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar. Varsayılan değer `unspecified` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="text-value"></a>Metin Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 `proxy` öğesi bir uygulama için ara sunucu tanımlar. Yapılandırma dosyasında bu öğe eksikse .NET Framework, Internet Explorer 'daki proxy ayarlarını kullanacaktır.  
  
 `proxyaddress` özniteliğinin değeri iyi biçimlendirilmiş bir Tekdüzen Kaynak göstergesi (URI) olmalıdır.  
  
 `scriptLocation` özniteliği, proxy yapılandırma betikleri otomatik algılamayı ifade eder. <xref:System.Net.WebProxy> sınıfı, Internet Explorer 'da **otomatik yapılandırma betiği kullan** seçeneği belirlendiğinde bir yapılandırma betiğini (genellikle WPAD. dat olarak adlandırılır) bulmaya çalışır. `bypassonlocal` herhangi bir değere ayarlanırsa, `scriptLocation` yok sayılır.
  
 2,0 sürümüne geçiş yapan .NET Framework sürüm 1,1 uygulamaları için `usesystemdefault` özniteliğini kullanın.  
  
 `proxyaddress` özniteliği geçersiz bir varsayılan proxy belirtiyorsa bir özel durum oluşturulur. Özel durumun <xref:System.Exception.InnerException%2A> özelliği, hatanın kök nedeni hakkında daha fazla bilgiye sahip olmalıdır.  
  
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
