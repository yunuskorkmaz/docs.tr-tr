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
ms.openlocfilehash: 1f0241b65c915dd5703ceea97dd5b07f88832003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698489"
---
# <a name="web-settings-schema"></a><span data-ttu-id="5431e-102">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5431e-102">Web Settings Schema</span></span>
<span data-ttu-id="5431e-103">Web ayarları, CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde davranışı uygulamak yürütme düzeyinde ASP.NET ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="5431e-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="5431e-104">Bu ayarlar, ASP.NET uygulamasının Web.config dosyasında belirtilen uygulama etki alanı türü ayarları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5431e-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="5431e-105">Web ayarları, .NET Framework sürümleri yükleme klasörlerinde bulunan Aspnet.config dosyalarında yer alır.</span><span class="sxs-lookup"><span data-stu-id="5431e-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="5431e-106">Örneğin, Aspnet.config dosyayı [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] aşağıdaki klasörde bulunan:</span><span class="sxs-lookup"><span data-stu-id="5431e-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="5431e-107">Web ayarları machine.config dosyasının, kök Web.config veya uygulama düzeyi Web.config dosyaları gibi diğer yapılandırma dosyalarını kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="5431e-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="5431e-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="5431e-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="5431e-109">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5431e-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="5431e-110">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5431e-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="5431e-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="5431e-111">Element</span></span>|<span data-ttu-id="5431e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5431e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5431e-113">\<System.Web ></span><span class="sxs-lookup"><span data-stu-id="5431e-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="5431e-114">ASP.NET barındırma katman kullandığı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5431e-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="5431e-115">\<ApplicationPool ></span><span class="sxs-lookup"><span data-stu-id="5431e-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="5431e-116">CPU ve katman barındırma ASP.NET tarafından yönetilen işlem genelinde davranışı uygulamak yürütme düzeyinde ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5431e-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5431e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5431e-117">See also</span></span>

- [<span data-ttu-id="5431e-118">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5431e-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
