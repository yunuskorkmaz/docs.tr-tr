---
description: 'Daha fazla bilgi edinin: IGCHost:: GetStats yöntemi'
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
ms.openlocfilehash: 564224d01e23c8ac1fe81025ee87dabc41ed5166
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709701"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="f5ca5-103">IGCHost::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="f5ca5-103">IGCHost::GetStats Method</span></span>

<span data-ttu-id="f5ca5-104">Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="f5ca5-104">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ca5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5ca5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5ca5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5ca5-106">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="f5ca5-107">[in, out] Çöp toplama sisteminin geçerli durumunun istatistiklerini içeren [cor_gc_stats](cor-gc-stats-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f5ca5-107">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5ca5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5ca5-108">Remarks</span></span>  

 <span data-ttu-id="f5ca5-109">İstatistikler, atık toplama sisteminin çalışmasını sağlamak için bir akıllı ayırma sistemi tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5ca5-109">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="f5ca5-110">Örneğin, ayırma sistemi istatistikleri inceledikten sonra, daha fazla bellek eklemesi veya bir koleksiyona zorlamak için ihtiyaç duymasını tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="f5ca5-110">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5ca5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5ca5-111">Requirements</span></span>  

 <span data-ttu-id="f5ca5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5ca5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5ca5-113">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="f5ca5-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f5ca5-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f5ca5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5ca5-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5ca5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ca5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5ca5-116">See also</span></span>

- [<span data-ttu-id="f5ca5-117">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5ca5-117">IGCHost Interface</span></span>](igchost-interface.md)
