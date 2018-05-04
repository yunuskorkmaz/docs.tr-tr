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
manager: markl
ms.openlocfilehash: 93d0d2ea5cf3b0329d9b1a03a233cff2d8133072
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="web-settings-schema"></a>Web Ayarları Şeması
Web ayarları CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde geçerli yürütme düzeyi ASP.NET ayarlarını belirtin. Bu ayarlar bir ASP.NET uygulaması Web.config dosyasında belirtilen uygulama etki alanı türü ayarları farklı.  
  
 Web ayarları, .NET Framework sürümleri için yükleme klasörlerde bulunan Aspnet.config dosyalarında bulunur. Örneğin, Aspnet.config dosyası için [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] aşağıdaki klasörde bulunmaktadır:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Web ayarları machine.config dosyasının, kök Web.config veya uygulama düzeyinde Web.config dosyaları gibi diğer yapılandırma dosyalarını kullanılmaz.  
  
 [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.Web > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.Web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET barındırma katman kullandığı bilgileri içerir.|  
|[\<ApplicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde geçerli yürütme düzeyi ASP.NET ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
