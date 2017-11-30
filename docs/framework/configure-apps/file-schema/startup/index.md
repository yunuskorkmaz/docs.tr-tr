---
title: "Başlangıç Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 61ea6d0c974683e73e835720cff48ff84169217e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="startup-settings-schema"></a><span data-ttu-id="f3247-102">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f3247-102">Startup Settings Schema</span></span>
<span data-ttu-id="f3247-103">Başlangıç ayarları uygulama çalışması gerektiğini ortak dil çalışma zamanı sürümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="f3247-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="f3247-104">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3247-104">Element</span></span>|<span data-ttu-id="f3247-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3247-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3247-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="f3247-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="f3247-107">Uygulamanın yalnızca sürüm 1.0 ortak dil çalışma zamanı desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3247-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f3247-108">Çalışma zamanı sürüm 1.1 ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="f3247-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="f3247-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="f3247-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="f3247-110">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3247-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="f3247-111">\<Başlangıç ></span><span class="sxs-lookup"><span data-stu-id="f3247-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="f3247-112">İçeren  **\<requiredRuntime >** ve  **\<supportedRuntime >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f3247-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3247-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3247-113">See Also</span></span>  
 [<span data-ttu-id="f3247-114">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f3247-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f3247-115">\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme</span><span class="sxs-lookup"><span data-stu-id="f3247-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
