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
ms.openlocfilehash: a2d2d6307136f0f8983e409d9f17fbcae1c55705
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760359"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="55fda-102">ICorThreadpool::CorCallOrQueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55fda-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>
<span data-ttu-id="55fda-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="55fda-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55fda-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="55fda-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="55fda-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55fda-105">Requirements</span></span>  
 <span data-ttu-id="55fda-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55fda-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55fda-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="55fda-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55fda-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="55fda-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55fda-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55fda-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fda-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55fda-110">See also</span></span>

- [<span data-ttu-id="55fda-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55fda-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
