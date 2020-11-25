---
title: ICorThreadpool::CorUnregisterWait Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 38b3655da75750ffc3ea1c7983ce3b549d76f087
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733981"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="3d4fc-102">ICorThreadpool::CorUnregisterWait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d4fc-102">ICorThreadpool::CorUnregisterWait Method</span></span>

<span data-ttu-id="3d4fc-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="3d4fc-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4fc-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d4fc-104">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3d4fc-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d4fc-105">Requirements</span></span>  

 <span data-ttu-id="3d4fc-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d4fc-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4fc-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3d4fc-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d4fc-108">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3d4fc-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d4fc-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4fc-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4fc-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d4fc-110">See also</span></span>

- [<span data-ttu-id="3d4fc-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d4fc-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
