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
# <a name="web-settings-schema"></a><span data-ttu-id="919a9-102">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="919a9-102">Web Settings Schema</span></span>
<span data-ttu-id="919a9-103">Web ayarları, CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde davranışı uygulamak yürütme düzeyinde ASP.NET ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="919a9-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="919a9-104">Bu ayarlar, ASP.NET uygulamasının Web.config dosyasında belirtilen uygulama etki alanı türü ayarları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="919a9-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="919a9-105">Web ayarları, .NET Framework sürümleri yükleme klasörlerinde bulunan Aspnet.config dosyalarında yer alır.</span><span class="sxs-lookup"><span data-stu-id="919a9-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="919a9-106">Örneğin, Aspnet.config dosyayı [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] aşağıdaki klasörde bulunan:</span><span class="sxs-lookup"><span data-stu-id="919a9-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="919a9-107">Web ayarları machine.config dosyasının, kök Web.config veya uygulama düzeyi Web.config dosyaları gibi diğer yapılandırma dosyalarını kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="919a9-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="919a9-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="919a9-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="919a9-109">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="919a9-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="919a9-110">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="919a9-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="919a9-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="919a9-111">Element</span></span>|<span data-ttu-id="919a9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="919a9-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="919a9-113">\<System.Web ></span><span class="sxs-lookup"><span data-stu-id="919a9-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="919a9-114">ASP.NET barındırma katman kullandığı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="919a9-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="919a9-115">\<ApplicationPool ></span><span class="sxs-lookup"><span data-stu-id="919a9-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="919a9-116">CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde davranışı uygulamak yürütme düzeyinde ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="919a9-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="919a9-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="919a9-117">See Also</span></span>  
 [<span data-ttu-id="919a9-118">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="919a9-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
