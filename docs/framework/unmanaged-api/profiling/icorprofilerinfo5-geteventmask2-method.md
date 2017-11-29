---
title: ICorProfilerInfo5::GetEventMask2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerInfo5.GetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da1c4c11adaac21e9769330ee24beceff64e020b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="654b0-102">ICorProfilerInfo5::GetEventMask2 Metodu</span><span class="sxs-lookup"><span data-stu-id="654b0-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="654b0-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="654b0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="654b0-104">Profil Oluşturucu ortak dil çalışma (CLR) bildirimlerini almak istediği geçerli olay kategorileri alır.</span><span class="sxs-lookup"><span data-stu-id="654b0-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="654b0-105">Tarafından sağlanmayan işlevsellik sağlar [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="654b0-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654b0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="654b0-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="654b0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="654b0-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="654b0-108">[out] Olayların kategorilerini belirler 4-bayt bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="654b0-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="654b0-109">Her bitin farklı yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="654b0-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="654b0-110">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="654b0-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="654b0-111">[out] Olayların kategorilerini belirler 4-bayt bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="654b0-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="654b0-112">Her bitin farklı yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="654b0-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="654b0-113">BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="654b0-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="654b0-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="654b0-114">Remarks</span></span>  
 <span data-ttu-id="654b0-115">`GetEventMask2` Yöntemi profil oluşturucu abone için hangi geri aramalar belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="654b0-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="654b0-116">Mantıksal OR, genellikle gerçekleştirdiğiniz `pdwEventsLow` ve `pdwEventsHigh` değerleri ve istediğiniz ayarlayın ve ardından çağırmak için herhangi bir yeni BITS [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="654b0-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="654b0-117">Bu yöntem için önerilen alternatiftir [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="654b0-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="654b0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="654b0-118">Requirements</span></span>  
 <span data-ttu-id="654b0-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="654b0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="654b0-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="654b0-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="654b0-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="654b0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="654b0-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="654b0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654b0-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="654b0-123">See Also</span></span>  
 [<span data-ttu-id="654b0-124">Icorprofilerınfo5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="654b0-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="654b0-125">SetEventMask2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="654b0-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
