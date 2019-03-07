---
title: IGCHost::GetStats Metodu
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b8af1de3daf08a8389a5b0e6ebb278646345f9b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482619"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="fe821-102">IGCHost::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="fe821-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="fe821-103">İstatistikleri çöp toplama sistemi için geçerli durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="fe821-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe821-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe821-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe821-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe821-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="fe821-106">[out içinde] Bir işaretçi bir [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) geçerli çöp toplama sistem durumu ile ilgili istatistikleri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="fe821-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe821-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe821-107">Remarks</span></span>  
 <span data-ttu-id="fe821-108">İstatistikleri çalışması çöp toplama sistemi yardımcı olmak için bir akıllı ayırma sistemi tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe821-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="fe821-109">Örneğin, daha fazla bellek ekleyin veya bir toplamayı zorlamak için gereken istatistiklerini gözden geçirdikten sonra ayırma sistem belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="fe821-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe821-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe821-110">Requirements</span></span>  
 <span data-ttu-id="fe821-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe821-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe821-112">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="fe821-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="fe821-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fe821-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe821-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe821-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe821-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe821-115">See also</span></span>
- [<span data-ttu-id="fe821-116">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe821-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
