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
ms.openlocfilehash: 09d273a81ed4f956508e4fadb628b28e18d00f90
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449569"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="a95d8-102">ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a95d8-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="a95d8-103">Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a95d8-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="a95d8-104">Bu yöntem, JıT kodlarını numaralandırmayan [ICorProfilerInfo3:: EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) yönteminin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="a95d8-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a95d8-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a95d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a95d8-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a95d8-107">dışı [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) numaralandırıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a95d8-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a95d8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a95d8-108">Remarks</span></span>  
 <span data-ttu-id="a95d8-109">Bu yöntem [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi gibi `JITCompilation` geri çağırmaları ile çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="a95d8-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="a95d8-110">Döndürülen sabit listesi `COR_PRF_FUNCTION::reJitId` alanı için değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a95d8-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="a95d8-111">Bu yöntemin yerini aldığı [ICorProfilerInfo3:: EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) yöntemi, `COR_PRF_FUNCTION::reJitId` alanı her zaman 0 olarak AYARLANDıĞı Için JIT kodlarını numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="a95d8-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="a95d8-112">`ICorProfilerInfo4::EnumJITedFunctions` yöntemi, `COR_PRF_FUNCTION::reJitId` alanı düzgün şekilde ayarlandığından JıT kimliklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="a95d8-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="a95d8-113">[ICorProfilerInfo4:: EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yönteminin bir çöp toplamayı tetikleyebileceğine, ancak [ICorProfilerInfo3:: EnumJITedFunctions metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="a95d8-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="a95d8-114">Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="a95d8-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a95d8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a95d8-115">Requirements</span></span>  
 <span data-ttu-id="a95d8-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a95d8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a95d8-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a95d8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a95d8-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a95d8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a95d8-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a95d8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95d8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a95d8-120">See also</span></span>

- [<span data-ttu-id="a95d8-121">EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a95d8-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="a95d8-122">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a95d8-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="a95d8-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a95d8-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a95d8-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a95d8-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
