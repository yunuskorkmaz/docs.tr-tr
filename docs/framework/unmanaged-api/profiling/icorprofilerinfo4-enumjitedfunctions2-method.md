---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: Enumjıtedfunctions2 yöntemi'
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
ms.openlocfilehash: 3740236cfe2bc7ecc6cd3bbeb3345c7510dd159f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686953"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="38d5c-103">ICorProfilerInfo4::EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38d5c-103">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>

<span data-ttu-id="38d5c-104">Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="38d5c-104">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="38d5c-105">Bu yöntem, JıT kodlarını numaralandırmayan [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) yönteminin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="38d5c-105">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d5c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38d5c-106">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38d5c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38d5c-107">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="38d5c-108">dışı [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) numaralandırıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38d5c-108">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38d5c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38d5c-109">Remarks</span></span>  

 <span data-ttu-id="38d5c-110">Bu yöntem `JITCompilation` [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) yöntemi gibi geri çağırmalar ile çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="38d5c-110">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="38d5c-111">Döndürülen sabit listesi alanın değerlerini içerir `COR_PRF_FUNCTION::reJitId` .</span><span class="sxs-lookup"><span data-stu-id="38d5c-111">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="38d5c-112">Bu yöntemin yerini aldığı [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) yöntemi, `COR_PRF_FUNCTION::reJitId` alanı her zaman 0 olarak ayarlandığı için JIT kodlarını numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="38d5c-112">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="38d5c-113">Bu `ICorProfilerInfo4::EnumJITedFunctions` Yöntem, `COR_PRF_FUNCTION::reJitId` alan düzgün şekılde ayarlandığından JIT kimliklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="38d5c-113">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="38d5c-114">[ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) yönteminin bir çöp toplamayı tetikleyebileceğine, ancak [ICorProfilerInfo3:: EnumJITedFunctions metodu](icorprofilerinfo3-enumjitedfunctions-method.md) olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="38d5c-114">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="38d5c-115">Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="38d5c-115">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38d5c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38d5c-116">Requirements</span></span>  

 <span data-ttu-id="38d5c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38d5c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d5c-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="38d5c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38d5c-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="38d5c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38d5c-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d5c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d5c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38d5c-121">See also</span></span>

- [<span data-ttu-id="38d5c-122">EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38d5c-122">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="38d5c-123">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38d5c-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="38d5c-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="38d5c-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="38d5c-125">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="38d5c-125">Profiling</span></span>](index.md)
