---
title: Web Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 461043dbb57043c5c18ea703d45f8b3ae487d271
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112289"
---
# <a name="web-settings-schema"></a>Web Ayarları Şeması
Web ayarları, CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde davranışı uygulamak yürütme düzeyinde ASP.NET ayarlarını belirtin. Bu ayarlar, ASP.NET uygulamasının Web.config dosyasında belirtilen uygulama etki alanı türü ayarları farklıdır.  
  
 Web ayarları, .NET Framework sürümleri yükleme klasörlerinde bulunan Aspnet.config dosyalarında yer alır. Örneğin, Aspnet.config dosyayı [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] aşağıdaki klasörde bulunan:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Web ayarları machine.config dosyasının, kök Web.config veya uygulama düzeyi Web.config dosyaları gibi diğer yapılandırma dosyalarını kullanılmaz.  
  
 [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.Web > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.Web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET barındırma katman kullandığı bilgileri içerir.|  
|[\<ApplicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde davranışı uygulamak yürütme düzeyinde ASP.NET ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
