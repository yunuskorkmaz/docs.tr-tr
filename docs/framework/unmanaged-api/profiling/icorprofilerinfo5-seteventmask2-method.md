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
ms.openlocfilehash: 1e1779c0f4f36b2d7b81832bc90cf5aee0b8a7df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130391"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="6f6d3-102">ICorProfilerInfo5::SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f6d3-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="6f6d3-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="6f6d3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6f6d3-104">Profil oluşturucunun, ortak dil çalışma zamanından (CLR) olay bildirimleri almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="6f6d3-105">[ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yönteminden daha fazla işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6d3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f6d3-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f6d3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f6d3-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="6f6d3-108">'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="6f6d3-109">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="6f6d3-110">Bitleri [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması içinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="6f6d3-111">'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="6f6d3-112">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="6f6d3-113">Bitleri [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması içinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f6d3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f6d3-114">Remarks</span></span>  
 <span data-ttu-id="6f6d3-115">`SetEventMask2` yöntemi, profil oluşturucunun abone olduğu geri çağırmaları ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="6f6d3-116">Genellikle, hangi bitlerin ayarlandığını öğrenmek için [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) yöntemini çağırır, `pdwEventsLow` ve `pdwEventsHigh` değerlerini ve ayarlamak istediğiniz tüm yeni bitleri gerçekleştirin ve ardından `SetEventMask2` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="6f6d3-117">Bu yöntem, [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yönteminin önerilen alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f6d3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f6d3-118">Requirements</span></span>  
 <span data-ttu-id="6f6d3-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f6d3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f6d3-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6f6d3-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f6d3-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6f6d3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f6d3-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6d3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6d3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f6d3-123">See also</span></span>

- [<span data-ttu-id="6f6d3-124">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f6d3-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="6f6d3-125">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f6d3-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
