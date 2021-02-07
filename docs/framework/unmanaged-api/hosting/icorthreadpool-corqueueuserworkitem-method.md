---
description: ': ICorThreadpool:: CorQueueUserWorkItem yöntemi hakkında daha fazla bilgi edinin'
title: ICorThreadpool::CorQueueUserWorkItem Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: fc0fc1dc3aa33bf11735fddd2c034af03f269f3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737780"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="9c7d0-103">ICorThreadpool::CorQueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c7d0-103">ICorThreadpool::CorQueueUserWorkItem Method</span></span>

<span data-ttu-id="9c7d0-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="9c7d0-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c7d0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c7d0-105">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9c7d0-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c7d0-106">Requirements</span></span>  

 <span data-ttu-id="9c7d0-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c7d0-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c7d0-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c7d0-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c7d0-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9c7d0-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c7d0-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c7d0-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c7d0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c7d0-111">See also</span></span>

- [<span data-ttu-id="9c7d0-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c7d0-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
