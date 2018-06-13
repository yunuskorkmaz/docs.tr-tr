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
ms.locfileid: "32767485"
---
# <a name="web-settings-schema"></a><span data-ttu-id="55a3e-102">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="55a3e-102">Web Settings Schema</span></span>
<span data-ttu-id="55a3e-103">Web ayarları CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde geçerli yürütme düzeyi ASP.NET ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="55a3e-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="55a3e-104">Bu ayarlar bir ASP.NET uygulaması Web.config dosyasında belirtilen uygulama etki alanı türü ayarları farklı.</span><span class="sxs-lookup"><span data-stu-id="55a3e-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="55a3e-105">Web ayarları, .NET Framework sürümleri için yükleme klasörlerde bulunan Aspnet.config dosyalarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="55a3e-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="55a3e-106">Örneğin, Aspnet.config dosyası için [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] aşağıdaki klasörde bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="55a3e-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="55a3e-107">Web ayarları machine.config dosyasının, kök Web.config veya uygulama düzeyinde Web.config dosyaları gibi diğer yapılandırma dosyalarını kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="55a3e-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="55a3e-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="55a3e-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="55a3e-109">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="55a3e-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="55a3e-110">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="55a3e-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="55a3e-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="55a3e-111">Element</span></span>|<span data-ttu-id="55a3e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55a3e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55a3e-113">\<System.Web ></span><span class="sxs-lookup"><span data-stu-id="55a3e-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="55a3e-114">ASP.NET barındırma katman kullandığı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="55a3e-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="55a3e-115">\<ApplicationPool ></span><span class="sxs-lookup"><span data-stu-id="55a3e-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="55a3e-116">CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde geçerli yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55a3e-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55a3e-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55a3e-117">See Also</span></span>  
 [<span data-ttu-id="55a3e-118">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="55a3e-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
