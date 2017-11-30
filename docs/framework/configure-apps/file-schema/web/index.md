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
# <a name="web-settings-schema"></a><span data-ttu-id="08337-102">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="08337-102">Web Settings Schema</span></span>
<span data-ttu-id="08337-103">Web ayarları CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde geçerli yürütme düzeyi ASP.NET ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="08337-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="08337-104">Bu ayarlar bir ASP.NET uygulaması Web.config dosyasında belirtilen uygulama etki alanı türü ayarları farklı.</span><span class="sxs-lookup"><span data-stu-id="08337-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="08337-105">Web ayarları, .NET Framework sürümleri için yükleme klasörlerde bulunan Aspnet.config dosyalarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="08337-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="08337-106">Örneğin, Aspnet.config dosyası için [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] aşağıdaki klasörde bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="08337-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="08337-107">Web ayarları machine.config dosyasının, kök Web.config veya uygulama düzeyinde Web.config dosyaları gibi diğer yapılandırma dosyalarını kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="08337-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="08337-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="08337-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="08337-109">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="08337-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="08337-110">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="08337-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="08337-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="08337-111">Element</span></span>|<span data-ttu-id="08337-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08337-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08337-113">\<System.Web ></span><span class="sxs-lookup"><span data-stu-id="08337-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="08337-114">ASP.NET barındırma katman kullandığı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="08337-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="08337-115">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="08337-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="08337-116">CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde geçerli yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08337-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08337-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08337-117">See Also</span></span>  
 [<span data-ttu-id="08337-118">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="08337-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
