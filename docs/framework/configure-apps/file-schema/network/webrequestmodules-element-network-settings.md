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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154549"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> Elemanı (Ağ Ayarları)
Ağ ana bilgisayarlarından bilgi istemek için kullanılacak modülleri belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
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
|[Ekle](add-element-for-webrequestmodules-network-settings.md)|Uygulamaya özel bir Web isteği modülü ekler.|  
|[Temizleyin](clear-element-for-webrequestmodules-network-settings.md)|Tüm kayıtlı Web istek modüllerini uygulamadan kaldırır.|  
|[Kaldırmak](remove-element-for-webrequestmodules-network-settings.md)|Özel bir Web isteği modüllerini uygulamadan kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework'ün ağa nasıl bağladığını belirten ayarlar içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `webRequestModules` ağ ana bilgisayarlarına bilgi isteklerini <xref:System.Net.WebRequest> işlemek için sınıfın torunlarını kaydeder. Web istek modülleri <xref:System.Net.IWebRequestCreate> arabirimi uygulamalıdır.  
  
 .NET Framework, URI'ler için `http://`,, `https://`ve `file://`. Varsayılan modülleri yalnızca yapılandırma dosyasına özel bir modül kaydederek geçersiz kılabilirsiniz.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte varsayılan HTTP modülü kaydedilir. Sürüm ve PublicKeyToken değerlerini belirtilen modül için doğru değerlerle değiştirmelisiniz.  
  
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
- [Ağ Ayarları Şeması](index.md)
