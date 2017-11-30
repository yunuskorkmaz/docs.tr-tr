---
title: "CoUninitializeEE İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeEE
helpviewer_keywords: CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d64064c29d2a03578305f71a37e759907814727e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="couninitializeee-function"></a><span data-ttu-id="68c81-102">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="68c81-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="68c81-103">`CoUninitializeEE`kullanılmıyor ve hiçbir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="68c81-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68c81-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="68c81-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68c81-105">Remarks</span></span>  
 <span data-ttu-id="68c81-106">Ortak dil çalışma zamanı yürütme altyapısı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="68c81-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="68c81-107">Yürütme altyapısı çağrısı kapatmaya [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="68c81-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c81-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68c81-108">See Also</span></span>  
 [<span data-ttu-id="68c81-109">Coınitializeee işlevi</span><span class="sxs-lookup"><span data-stu-id="68c81-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="68c81-110">Meta veri genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="68c81-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
