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
ms.openlocfilehash: c86786a34ff236fb57a1ea6bc4d00b9cd5c4a717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134892"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="710ff-102">IGCHost::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="710ff-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="710ff-103">Çöp toplama sisteminin geçerli durumunun istatistiklerini alır.</span><span class="sxs-lookup"><span data-stu-id="710ff-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="710ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="710ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="710ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="710ff-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="710ff-106">[in, out] Çöp toplama sisteminin geçerli durumunun istatistiklerini içeren bir [cor_gc_stats](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="710ff-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="710ff-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="710ff-107">Remarks</span></span>  
 <span data-ttu-id="710ff-108">İstatistikler, atık toplama sisteminin çalışmasını sağlamak için bir akıllı ayırma sistemi tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="710ff-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="710ff-109">Örneğin, ayırma sistemi istatistikleri inceledikten sonra, daha fazla bellek eklemesi veya bir koleksiyona zorlamak için ihtiyaç duymasını tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="710ff-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="710ff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="710ff-110">Requirements</span></span>  
 <span data-ttu-id="710ff-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="710ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="710ff-112">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="710ff-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="710ff-113">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="710ff-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="710ff-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="710ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="710ff-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="710ff-115">See also</span></span>

- [<span data-ttu-id="710ff-116">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="710ff-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
