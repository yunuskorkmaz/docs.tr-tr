---
title: <system.Net> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154562"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net> Öğesi (Ağ Ayarları)
.NET Framework'ün ağa nasıl bağladığını belirten ayarlar içerir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[kimlik doğrulamaModülleri](authenticationmodules-element-network-settings.md)|Internet isteklerini doğrulamak için kullanılan modülleri belirtir.|  
|[bağlantıYönetim](connectionmanagement-element-network-settings.md)|Bir Internet ana bilgisayara en fazla bağlantı sayısını belirtir.|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.|  
|[mailAyarlar](mailsettings-element-network-settings.md)|Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.|  
|[requestCaching](requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizmasını denetler.|  
|[ayarlar](settings-element-network-settings.md)|<xref:System.Net> Ve ilgili alt ad alanlarındaki sınıflar için temel ağ seçeneklerini yapılandırır.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Internet ana bilgisayarlarından bilgi istemek için kullanılacak modülleri belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Yapılandırma](../configuration-element.md)|Tüm ad alanlarının ayarlarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ \<system.net>](system-net-element-network-settings.md) <xref:System.Net> öğesi, ve ilgili alt ad alanlarındaki sınıflar için ayarlar içerir. Ayarlar, kimlik doğrulama modüllerini, bağlantı yönetimini, posta ayarlarını, proxy sunucusunu ve Internet istek modüllerini Internet ana bilgisayarlarından bilgi almak için yapılandırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sınıflar tarafından <xref:System.Net> kullanılan tipik bir yapılandırmayı gösterir.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Ayarları Şeması](index.md)
