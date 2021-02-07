---
description: 'Daha fazla bilgi edinin: başlangıç ayarları şeması'
title: Başlangıç ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: 268b8d8dc2598add61435dd6b07031aa06831737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726097"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="40933-103">Başlangıç ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="40933-103">Startup settings schema</span></span>

<span data-ttu-id="40933-104">Başlangıç ayarları, uygulamayı çalıştırması gereken ortak dil çalışma zamanının sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="40933-104">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="40933-105">Öğe</span><span class="sxs-lookup"><span data-stu-id="40933-105">Element</span></span>|<span data-ttu-id="40933-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40933-106">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="40933-107">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40933-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="40933-108">Çalışma zamanı sürüm 1,1 ile oluşturulan uygulamalar öğesini kullanmalıdır **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="40933-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="40933-109">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40933-109">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="40933-110">**\<requiredRuntime>** Ve öğelerini içerir **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="40933-110">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40933-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40933-111">See also</span></span>

- [<span data-ttu-id="40933-112">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="40933-112">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="40933-113">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="40933-113">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
