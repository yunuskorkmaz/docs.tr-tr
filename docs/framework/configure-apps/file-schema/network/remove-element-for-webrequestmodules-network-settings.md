---
title: '&lt;kaldırma&gt; öğesi webRequestModules (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 40eda14d4d578f10a77aa06843abd48f58c55f6a
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37073027"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a>&lt;kaldırma&gt; öğesi webRequestModules (ağ ayarları) için
Özel bir Web isteği modülü uygulamadan kaldırır.  
  
 \<Yapılandırma >  
\<system.net>  
\<webRequestModules >  
\<kaldırma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Özniteliği**|**Açıklama**|  
|-------------------|---------------------|  
|`prefix`|Bu Web isteği modülü tarafından işlenen isteklerin için URI öneki.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Ağ ana bilgisayarlardan bilgi istemek için kullanılacak modülleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `remove` Öğeyi belirtilen URI öneki için kayıtlı Web isteği modülü kaldırır.  
  
 Değeri `prefix` özniteliği geçerli bir URI--Örneğin, "http", baştaki karakterleri olmalıdır veya "`http://www.contoso.com` ".  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, HTTP için var olan bir Web isteği modül kaldırır ve ardından yeni özel bir Web isteği modülü HTTP istekleri www.contoso.com için kaydeder.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebRequest>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
