---
title: ICorThreadpool::CorCallOrQueueUserWorkItem Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCallOrQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallOrQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorCallOrQueueUserWorkItem method [.NET Framework hosting]
- CorCallOrQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: a2081223-84ca-4331-a8d3-9352f422f3e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f18fcd5be15794449cc6c60d5217db702159e34d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436669"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="89d30-102">ICorThreadpool::CorCallOrQueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89d30-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>
<span data-ttu-id="89d30-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="89d30-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89d30-104">Syntax</span></span>  
  
```  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="89d30-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89d30-105">Requirements</span></span>  
 <span data-ttu-id="89d30-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89d30-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89d30-107">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89d30-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89d30-108">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="89d30-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89d30-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d30-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d30-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89d30-110">See Also</span></span>  
 [<span data-ttu-id="89d30-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89d30-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
