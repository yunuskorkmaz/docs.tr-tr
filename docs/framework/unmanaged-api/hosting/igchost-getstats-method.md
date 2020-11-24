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
ms.openlocfilehash: 7e664d88bf9f67e936e693b663f27ca490da13ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670114"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="78133-102">IGCHost::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="78133-102">IGCHost::GetStats Method</span></span>

<span data-ttu-id="78133-103">Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="78133-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78133-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="78133-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78133-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78133-105">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="78133-106">[in, out] Çöp toplama sisteminin geçerli durumunun istatistiklerini içeren [cor_gc_stats](cor-gc-stats-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="78133-106">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78133-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78133-107">Remarks</span></span>  

 <span data-ttu-id="78133-108">İstatistikler, atık toplama sisteminin çalışmasını sağlamak için bir akıllı ayırma sistemi tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78133-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="78133-109">Örneğin, ayırma sistemi istatistikleri inceledikten sonra, daha fazla bellek eklemesi veya bir koleksiyona zorlamak için ihtiyaç duymasını tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="78133-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78133-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78133-110">Requirements</span></span>  

 <span data-ttu-id="78133-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78133-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78133-112">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="78133-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="78133-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="78133-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78133-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78133-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78133-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78133-115">See also</span></span>

- [<span data-ttu-id="78133-116">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78133-116">IGCHost Interface</span></span>](igchost-interface.md)
