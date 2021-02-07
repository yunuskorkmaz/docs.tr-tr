---
description: 'Daha fazla bilgi edinin: <webRequestModules> öğesi (ağ ayarları)'
title: <webRequestModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 851aec2bf38910239874cb5792239a48de6efb70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698433"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> Öğesi (Ağ Ayarları)

Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a>Syntax  
  
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
|[add](add-element-for-webrequestmodules-network-settings.md)|Uygulamaya özel bir Web isteği modülü ekler.|  
|[lediğiniz](clear-element-for-webrequestmodules-network-settings.md)|Tüm kayıtlı Web isteği modüllerini uygulamadan kaldırır.|  
|[temizlenmesine](remove-element-for-webrequestmodules-network-settings.md)|Uygulamadan özel bir Web istek modülünü kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `webRequestModules`Öğesi, <xref:System.Net.WebRequest> ağ konaklarına bilgi isteklerini işlemek üzere sınıfının alt öğelerini kaydeder. Web isteği modülleri <xref:System.Net.IWebRequestCreate> arabirimini gerçekleştirmelidir.  
  
 .NET Framework,, ve ile başlayan URI 'Ler için Web isteği modülleri içerir `http://` `https://` `file://` . Varsayılan modülleri yalnızca yapılandırma dosyasına özel bir modül kaydederek geçersiz kılabilirsiniz.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek varsayılan HTTP modülünü kaydeder. Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.  
  
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
- [Ağ ayarları şeması](index.md)
