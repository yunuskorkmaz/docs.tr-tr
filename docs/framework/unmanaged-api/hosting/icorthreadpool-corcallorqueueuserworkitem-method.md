---
title: "ICorThreadpool::CorCallOrQueueUserWorkItem Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorCallOrQueueUserWorkItem
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCallOrQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorCallOrQueueUserWorkItem method [.NET Framework hosting]
- CorCallOrQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: a2081223-84ca-4331-a8d3-9352f422f3e7
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb89ba5b13cb6c86f2d9b71d8ce822b79054301b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="ce940-102">ICorThreadpool::CorCallOrQueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce940-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>
<span data-ttu-id="ce940-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="ce940-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce940-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce940-104">Syntax</span></span>  
  
```  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ce940-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce940-105">Requirements</span></span>  
 <span data-ttu-id="ce940-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce940-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce940-107">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce940-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce940-108">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ce940-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce940-109">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce940-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce940-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce940-110">See Also</span></span>  
 [<span data-ttu-id="ce940-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce940-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
