---
title: "&lt;webRequestModules&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f0da0e8afb2a9f89116b0d30992ce27b8520271d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a>&lt;webRequestModules&gt; öğesi (ağ ayarları)
Ağ ana bilgisayarlardan bilgi istemek için kullanılacak modülleri belirtir.  
  
 \<Yapılandırma >  
\<System.NET >  
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
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Uygulamaya özel bir Web isteği modülü ekler.|  
|[Temizle](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Tüm kayıtlı Web isteği modülleri uygulamadan kaldırır.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Özel bir Web isteği modülü uygulamadan kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `webRequestModules` Öğesi alt öğeleri kaydeder <xref:System.Net.WebRequest> ağ ana bilgisi isteklerini işlemek için sınıf. Web isteği modülleri uygulanmalı <xref:System.Net.IWebRequestCreate> arabirimi.  
  
 .NET Framework http://, https:// ve file:// ile başlayan URI için Web isteği modüller içerir. Yapılandırma dosyasında yalnızca özel bir modüle kaydederek varsayılan modülleri geçersiz kılabilirsiniz.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan HTTP modülü kaydeder. Belirtilen modül için doğru değerlerle sürüm ve PublicKeyToken için değerleri değiştirmelisiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
