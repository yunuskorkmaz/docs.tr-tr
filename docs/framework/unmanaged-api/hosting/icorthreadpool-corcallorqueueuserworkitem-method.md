---
description: ': ICorThreadpool:: CorCallOrQueueUserWorkItem Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 630afab4eac94d0361b0c83c962ff6e7d59be42d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789586"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="f9ae6-103">ICorThreadpool::CorCallOrQueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9ae6-103">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>

<span data-ttu-id="f9ae6-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="f9ae6-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ae6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9ae6-105">Syntax</span></span>  
  
```cpp  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f9ae6-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9ae6-106">Requirements</span></span>  

 <span data-ttu-id="f9ae6-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9ae6-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9ae6-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9ae6-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9ae6-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f9ae6-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9ae6-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9ae6-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ae6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9ae6-111">See also</span></span>

- [<span data-ttu-id="f9ae6-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9ae6-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
