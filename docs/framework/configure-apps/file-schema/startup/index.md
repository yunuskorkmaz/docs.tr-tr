---
title: Başlangıç ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701521"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="86972-102">Başlangıç ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="86972-102">Startup settings schema</span></span>

<span data-ttu-id="86972-103">Başlangıç ayarları, uygulamayı çalıştırması gereken ortak dil çalışma zamanının sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="86972-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="86972-104">Öğe</span><span class="sxs-lookup"><span data-stu-id="86972-104">Element</span></span>|<span data-ttu-id="86972-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86972-105">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="86972-106">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86972-106">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="86972-107">Çalışma zamanı sürüm 1,1 ile oluşturulan uygulamalar öğesini kullanmalıdır **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="86972-107">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="86972-108">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86972-108">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="86972-109">**\<requiredRuntime>** Ve öğelerini içerir **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="86972-109">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86972-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86972-110">See also</span></span>

- [<span data-ttu-id="86972-111">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="86972-111">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="86972-112">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="86972-112">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
