---
title: ICorProfilerInfo5::SetEventMask2 Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc1cfadd809b7406845596ace78e308ccbf529a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456003"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="f4afc-102">ICorProfilerInfo5::SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4afc-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="f4afc-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="f4afc-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f4afc-104">Profil Oluşturucu ortak dil çalışma (CLR) olay bildirimlerini almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f4afc-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="f4afc-105">Daha fazla işlevsellik sağlar [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4afc-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4afc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4afc-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4afc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4afc-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="f4afc-108">[in] Olayların kategorilerini belirler 4-bayt değeri.</span><span class="sxs-lookup"><span data-stu-id="f4afc-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="f4afc-109">Her bitin farklı yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="f4afc-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="f4afc-110">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="f4afc-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="f4afc-111">[in] Olayların kategorilerini belirler 4-bayt değeri.</span><span class="sxs-lookup"><span data-stu-id="f4afc-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="f4afc-112">Her bitin farklı yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="f4afc-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="f4afc-113">BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="f4afc-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4afc-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4afc-114">Remarks</span></span>  
 <span data-ttu-id="f4afc-115">`SetEventMask2` Yöntemi için profil oluşturucu abone geri aramalar ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4afc-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="f4afc-116">Genellikle, arama [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) hangi BITS ayarlanır, belirlemek amacıyla yöntemi gerçekleştirmek, mantıksal veya kendi `pdwEventsLow` ve `pdwEventsHigh` değerleri ve istediğiniz ayarlayın ve ardından çağırmak için herhangi bir yeni BITS `SetEventMask2` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4afc-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="f4afc-117">Bu yöntem için önerilen alternatiftir [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4afc-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4afc-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4afc-118">Requirements</span></span>  
 <span data-ttu-id="f4afc-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4afc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4afc-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f4afc-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4afc-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4afc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4afc-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4afc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4afc-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4afc-123">See Also</span></span>  
 [<span data-ttu-id="f4afc-124">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4afc-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="f4afc-125">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4afc-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
