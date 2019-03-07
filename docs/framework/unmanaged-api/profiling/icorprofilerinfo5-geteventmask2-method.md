---
title: ICorProfilerInfo5::GetEventMask2 Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c68668c1d591a8fb53d04d632027b0d8effb0c42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474828"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="e797d-102">ICorProfilerInfo5::GetEventMask2 Metodu</span><span class="sxs-lookup"><span data-stu-id="e797d-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="e797d-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="e797d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e797d-104">Profil Oluşturucu ortak dil çalışma zamanından (CLR) bildirim almak istediği geçerli olay kategorileri alır.</span><span class="sxs-lookup"><span data-stu-id="e797d-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="e797d-105">Tarafından sağlanmayan işlevsellik sağlar [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e797d-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e797d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e797d-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e797d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e797d-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="e797d-108">[out] Olayların kategorilerini belirten bir 4 baytlık değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e797d-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="e797d-109">Farklı yetenek, davranış veya olay türü her bit denetler.</span><span class="sxs-lookup"><span data-stu-id="e797d-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="e797d-110">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e797d-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="e797d-111">[out] Olayların kategorilerini belirten bir 4 baytlık değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e797d-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="e797d-112">Farklı yetenek, davranış veya olay türü her bit denetler.</span><span class="sxs-lookup"><span data-stu-id="e797d-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="e797d-113">BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e797d-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e797d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e797d-114">Remarks</span></span>  
 <span data-ttu-id="e797d-115">`GetEventMask2` Yöntemi profil oluşturucu abone hangi geri çağırmaları belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e797d-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="e797d-116">Genellikle, mantıksal OR gerçekleştirdiğiniz `pdwEventsLow` ve `pdwEventsHigh` değerleri ve ayarlayın ve ardından çağırmak için istediğiniz herhangi bir yeni BITS [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e797d-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="e797d-117">Bu yöntem için önerilen alternatiftir [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e797d-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e797d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e797d-118">Requirements</span></span>  
 <span data-ttu-id="e797d-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e797d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e797d-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e797d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e797d-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e797d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e797d-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e797d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e797d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e797d-123">See also</span></span>
- [<span data-ttu-id="e797d-124">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e797d-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="e797d-125">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e797d-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
