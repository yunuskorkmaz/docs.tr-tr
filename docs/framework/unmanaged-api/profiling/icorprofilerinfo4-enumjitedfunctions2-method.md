---
title: ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d69b1c0bec89594a148d0d5d501dcab32280a2e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780883"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="06c66-102">ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06c66-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="06c66-103">Daha önce JIT olarak derlenmiş ve JIT yeniden derlenen tüm işlevler için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="06c66-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="06c66-104">Bu yöntem değiştirir [Icorprofilerınfo3::enumjıtedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) JIT yeniden derlenen kimlikleri numaralandırmaz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06c66-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06c66-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06c66-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06c66-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06c66-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="06c66-107">[out] Bir işaretçi [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="06c66-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06c66-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06c66-108">Remarks</span></span>  
 <span data-ttu-id="06c66-109">Bu yöntem ile çakışabilen `JITCompilation` gibi geri çağırmaları [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06c66-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="06c66-110">Döndürülen numaralandırma değerlerini içerir `COR_PRF_FUNCTION::reJitId` alan.</span><span class="sxs-lookup"><span data-stu-id="06c66-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="06c66-111">[Icorprofilerınfo3::enumjıtedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) değiştirir. Bu yöntem, yöntem değil listeleme JIT yeniden derlenen kimlikleri, çünkü `COR_PRF_FUNCTION::reJitId` alanı her zaman 0 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06c66-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="06c66-112">`ICorProfilerInfo4::EnumJITedFunctions` Yöntemi çünkü JIT yeniden derlenen kimlikleri, numaralandırma `COR_PRF_FUNCTION::reJitId` alanını düzgün bir şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06c66-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="06c66-113">Unutmayın [Icorprofilerınfo4::enumjıtedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemi, çöp toplama, tetikleyebilir, oysa [Icorprofilerınfo3::enumjıtedfunctions yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) erişemez.</span><span class="sxs-lookup"><span data-stu-id="06c66-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="06c66-114">Daha fazla bilgi için [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="06c66-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06c66-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06c66-115">Requirements</span></span>  
 <span data-ttu-id="06c66-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06c66-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06c66-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06c66-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06c66-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06c66-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06c66-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06c66-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c66-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06c66-120">See also</span></span>

- [<span data-ttu-id="06c66-121">EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06c66-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="06c66-122">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06c66-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="06c66-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="06c66-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="06c66-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="06c66-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
