---
title: ICorProfilerInfo4::GetReJITIDs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: 2ac645cbaaa45554568874653be016e4691bbd2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707483"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="00816-102">ICorProfilerInfo4::GetReJITIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00816-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>

<span data-ttu-id="00816-103">Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="00816-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="00816-104">Bu, daha sonra geri alınmış ancak henüz serbest bırakılmayan işlevlerin JıT yeniden derlenmiş sürümlerini içerir (örneğin, geri döndürülmüş işlevi içeren uygulama etki alanı hala kullanımda olduğunda).</span><span class="sxs-lookup"><span data-stu-id="00816-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00816-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="00816-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00816-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00816-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="00816-107">'ndaki `FunctionID` Sürümlerinin numaralandırılacağı işlev örneği.</span><span class="sxs-lookup"><span data-stu-id="00816-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="00816-108">'ndaki Dizide ayrılan JıT yeniden derleme kimliği sayısı `reJitIds` .</span><span class="sxs-lookup"><span data-stu-id="00816-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="00816-109">dışı JıT yeniden derlenen kimliklerinin gerçek sayısı.</span><span class="sxs-lookup"><span data-stu-id="00816-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="00816-110">dışı Belirtilen işlev için JıT-yeniden derleme kimliklerini içeren, arayan tarafından ayrılmış bir dizi.</span><span class="sxs-lookup"><span data-stu-id="00816-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00816-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00816-111">Remarks</span></span>  

 <span data-ttu-id="00816-112">`GetReJITIDs` belirli bir işlev örneği için etkin JıT-yeniden derlenmesi kimliklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="00816-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="00816-113">Bu, `ICorProfilerInfo` çağıran ayrılmış arabellekleri kabul eden diğer işlevlerle aynı kullanım modelini izler.</span><span class="sxs-lookup"><span data-stu-id="00816-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00816-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00816-114">Requirements</span></span>  

 <span data-ttu-id="00816-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00816-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00816-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00816-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00816-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="00816-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00816-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00816-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00816-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00816-119">See also</span></span>

- [<span data-ttu-id="00816-120">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00816-120">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="00816-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00816-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="00816-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="00816-122">Profiling</span></span>](index.md)
