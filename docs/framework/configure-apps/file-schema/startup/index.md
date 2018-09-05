---
title: Başlangıç Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 68f37e3efca784b94be90d5779c9bc402f144448
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530340"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="f0322-102">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f0322-102">Startup Settings Schema</span></span>
<span data-ttu-id="f0322-103">Başlangıç ayarları, uygulamanın çalışması gereken ortak dil çalışma zamanı sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="f0322-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="f0322-104">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0322-104">Element</span></span>|<span data-ttu-id="f0322-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0322-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0322-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="f0322-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="f0322-107">Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0322-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f0322-108">Çalışma zamanı sürüm 1.1 ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0322-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="f0322-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="f0322-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="f0322-110">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0322-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="f0322-111">\<Başlangıç ></span><span class="sxs-lookup"><span data-stu-id="f0322-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="f0322-112">İçeren  **\<requiredRuntime >** ve  **\<supportedRuntime >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f0322-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0322-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0322-113">See Also</span></span>  
 [<span data-ttu-id="f0322-114">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="f0322-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f0322-115">\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme</span><span class="sxs-lookup"><span data-stu-id="f0322-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
