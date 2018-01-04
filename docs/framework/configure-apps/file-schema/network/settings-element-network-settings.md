---
title: "&lt;ayarları&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6fd4b608964bca2e05424f2f76136fa69111adc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsettingsgt-element-network-settings"></a>&lt;ayarları&gt; öğesi (ağ ayarları)
Temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> ad alanı.  
  
 \<Yapılandırma >  
\<System.NET >  
\<Ayarlar >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[httpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|Tarafından kullanılan parametreler özelleştirir <xref:System.Net.HttpListener> sınıfı.|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|Web isteği parametreleri özelleştirir.|  
|[IPv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|Internet Protokolü sürüm 6 (IPv6) etkinleştirir destekler.|  
|[\<performanceCounter > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|Performans sayaçları ağ sağlar.|  
|[servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|Ağ kaynaklarına bağlantılarını yapılandırır.|  
|[Yuva](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|Yuva işlemleri tamamlama bağlantı noktalarını kullanacak olup olmadığını belirtir.|  
|[\<webProxyScript > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|Web proxy bulmak için kullanılan komut dosyası özelliklerini yapılandırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
