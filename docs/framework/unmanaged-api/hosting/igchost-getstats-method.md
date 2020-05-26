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
ms.openlocfilehash: 67668aa7ff9faf035a047e485a8a3c8a451f45b9
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805246"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="738f2-102">IGCHost::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="738f2-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="738f2-103">Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="738f2-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="738f2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="738f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="738f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="738f2-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="738f2-106">[in, out] Çöp toplama sisteminin geçerli durumunun istatistiklerini içeren [cor_gc_stats](cor-gc-stats-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="738f2-106">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="738f2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="738f2-107">Remarks</span></span>  
 <span data-ttu-id="738f2-108">İstatistikler, atık toplama sisteminin çalışmasını sağlamak için bir akıllı ayırma sistemi tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="738f2-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="738f2-109">Örneğin, ayırma sistemi istatistikleri inceledikten sonra, daha fazla bellek eklemesi veya bir koleksiyona zorlamak için ihtiyaç duymasını tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="738f2-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="738f2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="738f2-110">Requirements</span></span>  
 <span data-ttu-id="738f2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="738f2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="738f2-112">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="738f2-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="738f2-113">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="738f2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="738f2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="738f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738f2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="738f2-115">See also</span></span>

- [<span data-ttu-id="738f2-116">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="738f2-116">IGCHost Interface</span></span>](igchost-interface.md)
