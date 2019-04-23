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
ms.openlocfilehash: 8df9bbf2615776c2e023f03401785da95b2226eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204828"
---
# <a name="proxy-element-network-settings"></a>\<Proxy > öğesi (ağ ayarları)
Bir proxy sunucusu tanımlar.  
  
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
|`autoDetect`|Proxy otomatik olarak algılanır olup olmadığını belirtir. Varsayılan değer `unspecified` şeklindedir.|  
|`bypassonlocal`|Proxy için yerel kaynak atlanır olup olmadığını belirtir. Yerel kaynaklar yerel sunucuyu içerir (`http://localhost`, `http://loopback`, veya `http://127.0.0.1`) ve bir nokta olmadan bir URI (`http://webserver`). Varsayılan değer `unspecified` şeklindedir.|  
|`proxyaddress`|Proxy kullanmak için URI belirtir.|  
|`scriptLocation`|Yapılandırma betiğini konumunu belirtir. Kullanmayın `bypassonlocal` özniteliği bu öznitelikle. |  
|`usesystemdefault`|Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir. Varsa kümesine `true`, sonraki öznitelikleri, Internet Explorer proxy ayarlarını geçersiz kılınır. Varsayılan değer `unspecified` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="text-value"></a>Metin Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 `proxy` Öğesi, bir uygulama için bir proxy sunucusu tanımlar. Bu öğe yapılandırma dosyasından eksikse, .NET Framework Internet Explorer'ın proxy ayarlarını kullanır.  
  
 Değeri `proxyaddress` özniteliği bir biçimlendirilmiş Tekdüzen Kaynak göstergesi'nı (URI) olmalıdır.  
  
 `scriptLocation` Öznitelik proxy yapılandırma betiklerini otomatik algılanması için ifade eder. <xref:System.Net.WebProxy> Sınıfı, bir yapılandırma betiği (genellikle adlandırılmış Wpad.dat) ne zaman bulunacak deneyecek **otomatik yapılandırma betiği kullan** seçeneği, Internet Explorer'da belirlenir. Varsa `bypassonlocal` herhangi bir değere ayarlanmış `scriptLocation` göz ardı edilir.
  
 Kullanım `usesystemdefault` 2.0 sürümüne geçiş yapıyorsanız, .NET Framework sürüm 1.1 uygulamaları için özniteliği.  
  
 Bir özel durum `proxyaddress` özniteliği geçersiz varsayılan proxy belirtir. <xref:System.Exception.InnerException%2A> Özel durum özelliği, hatanın kök nedeni hakkında daha fazla bilgi olması gerekir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Internet Explorer proxy varsayılanlarından kullanır, proxy adresi belirtir ve yerel erişim proxy atlar.  
  
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
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
