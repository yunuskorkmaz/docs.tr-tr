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
ms.openlocfilehash: f8ebddf9a16b2eddbbc58342f68b517064e8d794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214643"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="74413-102">ICorProfilerInfo5::GetEventMask2 Metodu</span><span class="sxs-lookup"><span data-stu-id="74413-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="74413-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="74413-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="74413-104">Profil Oluşturucu ortak dil çalışma zamanından (CLR) bildirim almak istediği geçerli olay kategorileri alır.</span><span class="sxs-lookup"><span data-stu-id="74413-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="74413-105">Tarafından sağlanmayan işlevsellik sağlar [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74413-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74413-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74413-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74413-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74413-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="74413-108">[out] Olayların kategorilerini belirten bir 4 baytlık değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74413-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="74413-109">Farklı yetenek, davranış veya olay türü her bit denetler.</span><span class="sxs-lookup"><span data-stu-id="74413-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="74413-110">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="74413-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="74413-111">[out] Olayların kategorilerini belirten bir 4 baytlık değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74413-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="74413-112">Farklı yetenek, davranış veya olay türü her bit denetler.</span><span class="sxs-lookup"><span data-stu-id="74413-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="74413-113">BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="74413-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74413-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74413-114">Remarks</span></span>  
 <span data-ttu-id="74413-115">`GetEventMask2` Yöntemi profil oluşturucu abone hangi geri çağırmaları belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="74413-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="74413-116">Genellikle, mantıksal OR gerçekleştirdiğiniz `pdwEventsLow` ve `pdwEventsHigh` değerleri ve ayarlayın ve ardından çağırmak için istediğiniz herhangi bir yeni BITS [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74413-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="74413-117">Bu yöntem için önerilen alternatiftir [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74413-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74413-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74413-118">Requirements</span></span>  
 <span data-ttu-id="74413-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74413-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74413-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74413-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74413-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74413-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74413-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74413-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74413-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74413-123">See also</span></span>

- [<span data-ttu-id="74413-124">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74413-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="74413-125">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74413-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
