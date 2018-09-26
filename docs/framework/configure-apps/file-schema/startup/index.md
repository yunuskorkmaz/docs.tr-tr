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
ms.openlocfilehash: 4cdf6a051552ab1effd9c4d9c783297a62602f7a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204930"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="1ca57-102">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1ca57-102">Startup Settings Schema</span></span>
<span data-ttu-id="1ca57-103">Başlangıç ayarları, uygulamanın çalışması gereken ortak dil çalışma zamanı sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="1ca57-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="1ca57-104">Öğe</span><span class="sxs-lookup"><span data-stu-id="1ca57-104">Element</span></span>|<span data-ttu-id="1ca57-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ca57-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ca57-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="1ca57-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="1ca57-107">Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ca57-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="1ca57-108">Çalışma zamanı sürüm 1.1 ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="1ca57-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="1ca57-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="1ca57-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="1ca57-110">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ca57-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="1ca57-111">\<Başlangıç ></span><span class="sxs-lookup"><span data-stu-id="1ca57-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="1ca57-112">İçeren  **\<requiredRuntime >** ve  **\<supportedRuntime >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1ca57-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ca57-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ca57-113">See Also</span></span>  
 [<span data-ttu-id="1ca57-114">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="1ca57-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1ca57-115">\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme</span><span class="sxs-lookup"><span data-stu-id="1ca57-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
