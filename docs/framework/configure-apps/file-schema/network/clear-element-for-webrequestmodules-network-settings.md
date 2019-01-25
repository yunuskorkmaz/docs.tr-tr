---
title: '&lt;Temizle&gt; webRequestModules (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: ccb9a19d4e6d79a84123014746b659a7168b2158
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607010"
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a>&lt;Temizle&gt; webRequestModules (ağ ayarları) için
Tüm kayıtlı Web isteği modül uygulamadan kaldırır.  
  
 \<Yapılandırma >  
\<system.net>  
\<webRequestModules >  
\<Temizleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Ağ konaklarından bilgi istemek için modüller belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `clear` Öğeyi yapılandırma dosyası veya yapılandırma hiyerarşideki daha yüksek bir düzeyde daha önce tanımlanan tüm kayıtlı Web isteği modüllerini kaldırır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm Web isteği modülleri temizler ve ardından bir Web isteği modülü için HTTP kaydeder.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Net.WebRequest>
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
