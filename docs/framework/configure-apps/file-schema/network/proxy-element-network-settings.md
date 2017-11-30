---
title: "&lt;Proxy&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7178527f369c698b0ab53aa41cb28dd0126436b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltproxygt-element-network-settings"></a>&lt;Proxy&gt; öğesi (ağ ayarları)
Bir proxy sunucu tanımlar.  
  
 \<Yapılandırma >  
\<System.NET >  
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
  
|**Özniteliği**|**Açıklama**|  
|-------------------|---------------------|  
|`autoDetect`|Proxy otomatik olarak algılanır olup olmadığını belirtir. Varsayılan değer `unspecified` şeklindedir.|  
|`bypassonlocal`|Proxy için yerel kaynak atlanır olup olmadığını belirtir. Yerel kaynaklar yerel sunucunun (http://localhost, http://loopback veya http://127.0.0.1) ve bir süre (http://webserver) olmadan bir URI'yı içerir. Varsayılan değer `unspecified` şeklindedir.|  
|`proxyaddress`|Proxy kullanmak için URI belirtir.|  
|`scriptLocation`|Yapılandırma komut dosyası konumunu belirtir.|  
|`usesystemdefault`|Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir. Varsa kümesine `true`, sonraki öznitelikleri Internet Explorer proxy ayarları geçersiz kılar. Varsayılan değer `unspecified` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusu yapılandırır.|  
  
## <a name="text-value"></a>Metin Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 `proxy` Öğe, bir uygulama için bir proxy sunucusu tanımlar. Bu öğe yapılandırma dosyasından eksikse, .NET Framework Internet Explorer proxy ayarlarını kullanır.  
  
 Değeri `proxyaddress` özniteliği bir doğru biçimlendirilmiş Tekdüzen Kaynak göstergesi'nı (URI) olmalıdır.  
  
 `scriptLocation` Özniteliği proxy yapılandırma komut otomatik algılama için başvuruyor. <xref:System.Net.WebProxy> Sınıfı bulmaya çalışır bir yapılandırma betiğini (genellikle adlandırılmış Wpad.dat) ne zaman **otomatik yapılandırma betiği kullan** seçeneği, Internet Explorer'da belirlenir.  
  
 Kullanım `usesystemdefault` özniteliği sürüm 2.0 geçirme .NET Framework sürüm 1.1 uygulamaları için.  
  
 Bir özel durum `proxyaddress` özniteliği geçersiz varsayılan proxy belirtir. <xref:System.Exception.InnerException%2A> Özel durum özelliği hatasının kök nedeni hakkında daha fazla bilgi sahip olmalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan Internet Explorer proxy adlardan kullanır, proxy adresi belirtir ve yerel erişim için proxy atlar.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
