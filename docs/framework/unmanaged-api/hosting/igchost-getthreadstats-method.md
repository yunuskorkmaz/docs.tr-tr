---
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
ms.openlocfilehash: c48b580e632d67db5a9826c210415adab1bdba96
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670075"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="cfebb-102">IGCHost::GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfebb-102">IGCHost::GetThreadStats Method</span></span>

<span data-ttu-id="cfebb-103">Çöp toplama için iş parçacığı başına istatistikleri alır.</span><span class="sxs-lookup"><span data-stu-id="cfebb-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfebb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cfebb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfebb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfebb-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="cfebb-106">'ndaki İstatistiklerin alınacağı iş parçacığını belirten bir fiber tanımlama bilgisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfebb-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="cfebb-107">[in, out] Belirtilen iş parçacığı için çöp toplama istatistiklerini içeren [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfebb-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfebb-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfebb-108">Requirements</span></span>  

 <span data-ttu-id="cfebb-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfebb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfebb-110">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="cfebb-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cfebb-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cfebb-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfebb-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfebb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfebb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfebb-113">See also</span></span>

- [<span data-ttu-id="cfebb-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfebb-114">IGCHost Interface</span></span>](igchost-interface.md)
