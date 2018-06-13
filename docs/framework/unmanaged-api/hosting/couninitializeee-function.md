---
title: CoUninitializeEE İşlevi
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73fa281d28e9b5362ff386b55b07dd431f1915f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429188"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="b3180-102">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="b3180-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="b3180-103">`CoUninitializeEE` kullanılmıyor ve hiçbir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3180-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3180-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3180-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3180-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3180-105">Remarks</span></span>  
 <span data-ttu-id="b3180-106">Ortak dil çalışma zamanı yürütme altyapısı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b3180-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="b3180-107">Yürütme altyapısı çağrısı kapatmaya [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="b3180-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3180-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3180-108">See Also</span></span>  
 [<span data-ttu-id="b3180-109">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="b3180-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="b3180-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b3180-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
