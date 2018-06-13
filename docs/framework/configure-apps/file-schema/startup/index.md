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
ms.openlocfilehash: 59f0441b79244eb529be338495c32af886a5f2b3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745103"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="6aeaa-102">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6aeaa-102">Startup Settings Schema</span></span>
<span data-ttu-id="6aeaa-103">Başlangıç ayarları uygulama çalışması gerektiğini ortak dil çalışma zamanı sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="6aeaa-104">Öğe</span><span class="sxs-lookup"><span data-stu-id="6aeaa-104">Element</span></span>|<span data-ttu-id="6aeaa-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6aeaa-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aeaa-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="6aeaa-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="6aeaa-107">Uygulamanın yalnızca sürüm 1.0 ortak dil çalışma zamanı desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="6aeaa-108">Çalışma zamanı sürüm 1.1 ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="6aeaa-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="6aeaa-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="6aeaa-110">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="6aeaa-111">\<Başlangıç ></span><span class="sxs-lookup"><span data-stu-id="6aeaa-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="6aeaa-112">İçeren  **\<requiredRuntime >** ve  **\<supportedRuntime >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6aeaa-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-113">See Also</span></span>  
 [<span data-ttu-id="6aeaa-114">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="6aeaa-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6aeaa-115">\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme</span><span class="sxs-lookup"><span data-stu-id="6aeaa-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
