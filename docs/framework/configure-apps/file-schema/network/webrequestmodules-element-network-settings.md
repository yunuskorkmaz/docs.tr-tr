---
title: <webRequestModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: fd7c5765665345906597963f8a4b2dbf7fcc7227
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288853"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules > öğesi (ağ ayarları)
Ağ konaklarından bilgi istemek için modüller belirtir.  
  
 \<Yapılandırma >  
\<system.net>  
\<webRequestModules >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Uygulamaya özel bir Web isteği modülü ekler.|  
|[Temizle](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Tüm kayıtlı Web isteği modül uygulamadan kaldırır.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Özel bir Web isteği modülü uygulamadan kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `webRequestModules` Öğenin alt öğeleri kaydeder <xref:System.Net.WebRequest> ağ Konaklara bilgi isteklerini işlemek için sınıf. Web isteği modülleri uygulanmalı <xref:System.Net.IWebRequestCreate> arabirimi.  
  
 .NET Framework ile başlayan bir URI'leri için Web isteği modüllerini içerir `http://`, `https://`, ve `file://`. Yapılandırma dosyasında özel bir modülü yalnızca kaydederek varsayılan modülleri geçersiz kılabilirsiniz.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan HTTP modülü kaydeder. Belirtilen modül için doğru değerlerle PublicKeyToken ve Version değerleri değiştirmelisiniz.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
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
- <xref:System.Net.IWebRequestCreate>
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
