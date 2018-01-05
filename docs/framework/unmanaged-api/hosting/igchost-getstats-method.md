---
title: IGCHost::GetStats Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d105b0aed9c47d5e2d8ad664744e6424db63961
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="e056d-102">IGCHost::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="e056d-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="e056d-103">İstatistikleri çöp toplama sistemi için geçerli durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="e056d-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e056d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e056d-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e056d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e056d-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="e056d-106">[içinde out] Bir işaretçi bir [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) çöp toplama sistemi geçerli durumu ile ilgili istatistikleri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="e056d-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e056d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e056d-107">Remarks</span></span>  
 <span data-ttu-id="e056d-108">İstatistikleri çalışması çöp toplama sistemi yardımcı olmak için bir akıllı ayırma sistem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e056d-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="e056d-109">Örneğin, daha fazla bellek ekleyin veya bir koleksiyon zorlamak için gereken istatistikleri gözden geçirdikten sonra ayırma sistemi belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e056d-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e056d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e056d-110">Requirements</span></span>  
 <span data-ttu-id="e056d-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e056d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e056d-112">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="e056d-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e056d-113">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e056d-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e056d-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e056d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e056d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e056d-115">See Also</span></span>  
 [<span data-ttu-id="e056d-116">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e056d-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
