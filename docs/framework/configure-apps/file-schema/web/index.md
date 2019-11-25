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
ms.openlocfilehash: 030841330ff37cddb0c9e3e466a55a4be098e784
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088786"
---
# <a name="web-settings-schema"></a>Web Ayarları Şeması
Web ayarları, ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir. Bu ayarlar, bir ASP.NET uygulamasının Web. config dosyasında belirtilen uygulama etki alanı türü ayarlarından farklıdır.  
  
Web ayarları, .NET Framework sürümleri için yükleme klasörlerinde bulunan Aspnet. config dosyalarında bulunur. Örneğin, .NET Framework 2,0 için ASPNET. config dosyası aşağıdaki klasörsdır:  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Web ayarları, Machine. config dosyası, kök Web. config veya uygulama düzeyi Web. config dosyaları gibi diğer yapılandırma dosyalarında kullanılmaz.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. web >\<** ](system-web-element-web-settings.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<applicationPool >** ](applicationpool-element-web-settings.md)

|Öğe|Açıklama|  
|-------------|-----------------|  
|[System. Web > \<](system-web-element-web-settings.md)|ASP.NET barındırma katmanının kullandığı bilgileri içerir.|  
|[\<applicationPool >](applicationpool-element-web-settings.md)|ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
