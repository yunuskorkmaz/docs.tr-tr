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
ms.openlocfilehash: 6046ff8486b356ca781a42a34a5a18bdae8c4c73
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690024"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="0a44f-102">ICorThreadpool::CorCallOrQueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a44f-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>

<span data-ttu-id="0a44f-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="0a44f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a44f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a44f-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0a44f-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a44f-105">Requirements</span></span>  

 <span data-ttu-id="0a44f-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a44f-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a44f-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a44f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a44f-108">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0a44f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a44f-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a44f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a44f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a44f-110">See also</span></span>

- [<span data-ttu-id="0a44f-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a44f-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
