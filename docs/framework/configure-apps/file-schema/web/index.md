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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088786"
---
# <a name="web-settings-schema"></a><span data-ttu-id="81cf5-102">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="81cf5-102">Web Settings Schema</span></span>
<span data-ttu-id="81cf5-103">Web ayarları, ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81cf5-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="81cf5-104">Bu ayarlar, bir ASP.NET uygulamasının Web. config dosyasında belirtilen uygulama etki alanı türü ayarlarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="81cf5-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="81cf5-105">Web ayarları, .NET Framework sürümleri için yükleme klasörlerinde bulunan Aspnet. config dosyalarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="81cf5-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="81cf5-106">Örneğin, .NET Framework 2,0 için ASPNET. config dosyası aşağıdaki klasörsdır:</span><span class="sxs-lookup"><span data-stu-id="81cf5-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="81cf5-107">Web ayarları, Machine. config dosyası, kök Web. config veya uygulama düzeyi Web. config dosyaları gibi diğer yapılandırma dosyalarında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="81cf5-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|<span data-ttu-id="81cf5-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="81cf5-108">Element</span></span>|<span data-ttu-id="81cf5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81cf5-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="81cf5-110">ASP.NET barındırma katmanının kullandığı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="81cf5-110">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="81cf5-111">ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81cf5-111">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81cf5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81cf5-112">See also</span></span>

- [<span data-ttu-id="81cf5-113">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="81cf5-113">Configuration File Schema</span></span>](../index.md)
