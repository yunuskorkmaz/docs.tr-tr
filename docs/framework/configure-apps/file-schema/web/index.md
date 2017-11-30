---
title: "Web Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efdfba94bd2d2a64b3434c97f30a035f210fda9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
|[\<applicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde geçerli yürütme düzeyi ASP.NET ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
