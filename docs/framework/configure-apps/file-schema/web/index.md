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
ms.openlocfilehash: c3ac9b42aeff3f7b26f0b36480bc75ceda39e7e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185606"
---
# <a name="web-settings-schema"></a>Web Ayarları Şeması

Web ayarları, ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir. Bu ayarlar, bir ASP.NET uygulamasının Web.config dosyasında belirtilen uygulama etki alanı türü ayarlarından farklıdır.  
  
Web ayarları, .NET Framework sürümleri için yükleme klasörlerinde bulunan Aspnet.config dosyalarında bulunur. Örneğin, .NET Framework 2,0 Aspnet.config dosyası aşağıdaki klasörde yer verilmiştir:  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Web ayarları, machine.config dosyası, kök Web.config veya uygulama düzeyi Web.config dosyaları gibi başka herhangi bir yapılandırma dosyasında kullanılmaz.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|ASP.NET barındırma katmanının kullandığı bilgileri içerir.|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma dosyası şeması](../index.md)
