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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f86385ba4f4186d14994a2028ee11c42127546
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108361"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="78b4a-102">IGCHost::GetThreadStats Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78b4a-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="78b4a-103">Çöp toplama iş parçacığı başına istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="78b4a-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78b4a-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b4a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78b4a-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="78b4a-106">[in] İş parçacığı istatistiklerini almak istediğiniz belirten bir fiber tanımlama bilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="78b4a-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="78b4a-107">[out içinde] Bir işaretçi bir [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) belirtilen iş parçacığı çöp toplama istatistikleri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="78b4a-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b4a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78b4a-108">Requirements</span></span>  
 <span data-ttu-id="78b4a-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78b4a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78b4a-110">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="78b4a-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="78b4a-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="78b4a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="78b4a-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="78b4a-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="78b4a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78b4a-113">See also</span></span>

- [<span data-ttu-id="78b4a-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78b4a-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
