---
title: "ICorProfilerInfo5::SetEventMask2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e53ad9d297656e26f8ba0e9d7669711a3f44ef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="67fbc-102">ICorProfilerInfo5::SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67fbc-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="67fbc-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="67fbc-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="67fbc-104">Profil Oluşturucu ortak dil çalışma (CLR) olay bildirimlerini almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="67fbc-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="67fbc-105">Daha fazla işlevsellik sağlar [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67fbc-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67fbc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67fbc-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67fbc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67fbc-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="67fbc-108">[in] Olayların kategorilerini belirler 4-bayt değeri.</span><span class="sxs-lookup"><span data-stu-id="67fbc-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="67fbc-109">Her bitin farklı yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="67fbc-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="67fbc-110">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="67fbc-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="67fbc-111">[in] Olayların kategorilerini belirler 4-bayt değeri.</span><span class="sxs-lookup"><span data-stu-id="67fbc-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="67fbc-112">Her bitin farklı yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="67fbc-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="67fbc-113">BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="67fbc-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67fbc-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67fbc-114">Remarks</span></span>  
 <span data-ttu-id="67fbc-115">`SetEventMask2` Yöntemi için profil oluşturucu abone geri aramalar ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67fbc-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="67fbc-116">Genellikle, arama [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) hangi BITS ayarlanır, belirlemek amacıyla yöntemi gerçekleştirmek, mantıksal veya kendi `pdwEventsLow` ve `pdwEventsHigh` değerleri ve istediğiniz ayarlayın ve ardından çağırmak için herhangi bir yeni BITS `SetEventMask2` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67fbc-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="67fbc-117">Bu yöntem için önerilen alternatiftir [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67fbc-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67fbc-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67fbc-118">Requirements</span></span>  
 <span data-ttu-id="67fbc-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67fbc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67fbc-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67fbc-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67fbc-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67fbc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67fbc-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67fbc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fbc-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67fbc-123">See Also</span></span>  
 [<span data-ttu-id="67fbc-124">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67fbc-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="67fbc-125">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67fbc-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
