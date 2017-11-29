---
title: IGCHost::GetThreadStats Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetThreadStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7bfd6b89c3220e071a477e0c5b85e4ee57289762
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="540d6-102">IGCHost::GetThreadStats Metodu</span><span class="sxs-lookup"><span data-stu-id="540d6-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="540d6-103">İş parçacığı başına istatistiklerini atık toplama için alır.</span><span class="sxs-lookup"><span data-stu-id="540d6-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="540d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="540d6-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="540d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="540d6-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="540d6-106">[in] İş parçacığı istatistiklerini almak üzere belirten bir fiber tanımlama bilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="540d6-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="540d6-107">[içinde out] Bir işaretçi bir [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) belirtilen iş parçacığı atık toplama istatistikleri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="540d6-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="540d6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="540d6-108">Requirements</span></span>  
 <span data-ttu-id="540d6-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="540d6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="540d6-110">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="540d6-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="540d6-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="540d6-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="540d6-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="540d6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540d6-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="540d6-113">See Also</span></span>  
 [<span data-ttu-id="540d6-114">Igchost arabirimi</span><span class="sxs-lookup"><span data-stu-id="540d6-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
