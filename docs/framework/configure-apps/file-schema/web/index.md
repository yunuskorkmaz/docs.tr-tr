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
ms.openlocfilehash: d53d3a105203addfacb1c982e0960bd12996f571
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941419"
---
# <a name="web-settings-schema"></a><span data-ttu-id="d54b7-102">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d54b7-102">Web Settings Schema</span></span>
<span data-ttu-id="d54b7-103">Web ayarları, ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d54b7-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="d54b7-104">Bu ayarlar, bir ASP.NET uygulamasının Web. config dosyasında belirtilen uygulama etki alanı türü ayarlarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d54b7-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="d54b7-105">Web ayarları, .NET Framework sürümleri için yükleme klasörlerinde bulunan Aspnet. config dosyalarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="d54b7-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="d54b7-106">Örneğin, .NET Framework 2,0 için ASPNET. config dosyası aşağıdaki klasörsdır:</span><span class="sxs-lookup"><span data-stu-id="d54b7-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="d54b7-107">Web ayarları, Machine. config dosyası, kök Web. config veya uygulama düzeyi Web. config dosyaları gibi diğer yapılandırma dosyalarında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d54b7-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="d54b7-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="d54b7-108">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="d54b7-109">\<System. Web > öğesi (Web ayarları)</span><span class="sxs-lookup"><span data-stu-id="d54b7-109">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)  
  
 [<span data-ttu-id="d54b7-110">\<applicationPool > öğesi (Web ayarları)</span><span class="sxs-lookup"><span data-stu-id="d54b7-110">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="d54b7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="d54b7-111">Element</span></span>|<span data-ttu-id="d54b7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d54b7-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d54b7-113">\<System. Web ></span><span class="sxs-lookup"><span data-stu-id="d54b7-113">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="d54b7-114">ASP.NET barındırma katmanının kullandığı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d54b7-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="d54b7-115">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="d54b7-115">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="d54b7-116">ASP.NET barındırma katmanı tarafından yönetilen işlem genelinde davranışa uygulanan CPU ve yürütme düzeyi ASP.NET ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d54b7-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d54b7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d54b7-117">See also</span></span>

- [<span data-ttu-id="d54b7-118">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d54b7-118">Configuration File Schema</span></span>](../index.md)
