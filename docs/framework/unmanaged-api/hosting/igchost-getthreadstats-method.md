---
description: 'Daha fazla bilgi edinin: IGCHost:: GetThreadStats Yöntemi'
title: IGCHost::GetThreadStats Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 2d923560e915a0c88035caad70ad91149d793cb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709665"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="a6f7b-103">IGCHost::GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6f7b-103">IGCHost::GetThreadStats Method</span></span>

<span data-ttu-id="a6f7b-104">Çöp toplama için iş parçacığı başına istatistikleri alır.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-104">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f7b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6f7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6f7b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6f7b-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="a6f7b-107">'ndaki İstatistiklerin alınacağı iş parçacığını belirten bir fiber tanımlama bilgisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-107">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="a6f7b-108">[in, out] Belirtilen iş parçacığı için çöp toplama istatistiklerini içeren [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-108">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6f7b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6f7b-109">Requirements</span></span>  

 <span data-ttu-id="a6f7b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6f7b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f7b-111">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="a6f7b-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a6f7b-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a6f7b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6f7b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f7b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f7b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-114">See also</span></span>

- [<span data-ttu-id="a6f7b-115">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6f7b-115">IGCHost Interface</span></span>](igchost-interface.md)
