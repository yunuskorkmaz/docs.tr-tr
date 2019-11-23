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
ms.openlocfilehash: 810e942394c75c192e4423afe4c674ef3a2b9900
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697501"
---
# <a name="systemnet-element-network-settings"></a>\<sistem .net > öğesi (ağ ayarları)
.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
**System. net >\<** &nbsp;&nbsp;  
  
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
|[authenticationModules](authenticationmodules-element-network-settings.md)|Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Bir Internet ana bilgisayarına en fazla bağlantı sayısını belirtir.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
|[mailSettings](mailsettings-element-network-settings.md)|Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.|  
|[requestCaching](requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizmasını denetler.|  
|[Ayarlar](settings-element-network-settings.md)|<xref:System.Net> ve ilgili alt ad alanlarında sınıflar için temel ağ seçeneklerini yapılandırır.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Internet konaklarından bilgi istemek için kullanılacak modülleri belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[yapılandırmada](../configuration-element.md)|Tüm ad alanları için ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [\<System. net >](system-net-element-network-settings.md) öğesi, <xref:System.Net> ve ilgili alt ad alanlarındaki sınıfların ayarlarını içerir. Ayarlar, Internet konaklarından bilgi almak için kimlik doğrulama modüllerini, bağlantı yönetimini, posta ayarlarını, proxy sunucusunu ve Internet istek modüllerini yapılandırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Net> sınıfları tarafından kullanılan tipik bir yapılandırma gösterilmektedir.  
  
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
