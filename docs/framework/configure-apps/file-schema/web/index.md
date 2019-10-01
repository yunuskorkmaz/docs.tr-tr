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
ms.openlocfilehash: 71b9e46a8c2d60c853af63ee78e2ed5dbe6e98f4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699148"
---
# <a name="web-settings-schema"></a>Web Ayarları Şeması
Web ayarları, ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir. Bu ayarlar, bir ASP.NET uygulamasının Web. config dosyasında belirtilen uygulama etki alanı türü ayarlarından farklıdır.  
  
Web ayarları, .NET Framework sürümleri için yükleme klasörlerinde bulunan Aspnet. config dosyalarında bulunur. Örneğin, .NET Framework 2,0 için ASPNET. config dosyası aşağıdaki klasörsdır:  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Web ayarları, Machine. config dosyası, kök Web. config veya uygulama düzeyi Web. config dosyaları gibi diğer yapılandırma dosyalarında kullanılmaz.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. Web >** ](system-web-element-web-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<applicationpool >** ](applicationpool-element-web-settings.md)  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[@no__t -1System. Web >](system-web-element-web-settings.md)|ASP.NET barındırma katmanının kullandığı bilgileri içerir.|  
|[\<applicationPool >](applicationpool-element-web-settings.md)|ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
