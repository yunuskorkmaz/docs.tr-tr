---
description: 'Daha fazla bilgi edinin: Web ayarları şeması'
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
ms.openlocfilehash: 262a53ae062788143cbacdc1012085186f4c9652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681922"
---
# <a name="web-settings-schema"></a><span data-ttu-id="7f6be-103">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7f6be-103">Web Settings Schema</span></span>

<span data-ttu-id="7f6be-104">Web ayarları, ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f6be-104">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="7f6be-105">Bu ayarlar, bir ASP.NET uygulamasının Web.config dosyasında belirtilen uygulama etki alanı türü ayarlarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7f6be-105">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="7f6be-106">Web ayarları, .NET Framework sürümleri için yükleme klasörlerinde bulunan Aspnet.config dosyalarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="7f6be-106">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="7f6be-107">Örneğin, .NET Framework 2,0 Aspnet.config dosyası aşağıdaki klasörde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7f6be-107">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="7f6be-108">Web ayarları, machine.config dosyası, kök Web.config veya uygulama düzeyi Web.config dosyaları gibi başka herhangi bir yapılandırma dosyasında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="7f6be-108">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|<span data-ttu-id="7f6be-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f6be-109">Element</span></span>|<span data-ttu-id="7f6be-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f6be-110">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="7f6be-111">ASP.NET barındırma katmanının kullandığı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="7f6be-111">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="7f6be-112">ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f6be-112">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f6be-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f6be-113">See also</span></span>

- [<span data-ttu-id="7f6be-114">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="7f6be-114">Configuration File Schema</span></span>](../index.md)
