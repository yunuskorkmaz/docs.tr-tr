---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb7c8fa40d260e45ae536f1b58c6ab360f35448e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550649"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="1d534-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d534-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="1d534-103">Profil Oluşturucu uygulanan işlevleri güncelleştirilmiş sürümlerine ilişkin "enter", "Ayrıl" ve "tailcall" hooks yönetilen işlevlerin çağrılmasına belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d534-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d534-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d534-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d534-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d534-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="1d534-106">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1d534-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="1d534-107">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1d534-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="1d534-108">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1d534-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d534-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d534-109">Remarks</span></span>  
 <span data-ttu-id="1d534-110">`SetEnterLeaveFunctionHooks2` Yöntemi benzer [Icorprofilerınfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1d534-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="1d534-111">Önceki eski sürümleri enter/bırakma/tailcall geri çağırmaları kullanılacak işlevleri belirtmek için daha yeni sürümleri enter/bırakma/tailcall geri çağrıları ve ikinci kullanılacak işlevleri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d534-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="1d534-112">Bir kerede yalnızca bir dizi geri çağırmaları etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d534-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="1d534-113">Bu nedenle, her ikisi de bir profil oluşturucu çağırırsa `ICorProfilerInfo::SetEnterLeaveFunctionHooks` ve `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d534-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="1d534-114">`SetEnterLeaveFunctionHooks2` Yöntemi yalnızca profil oluşturucuyu 's adlı [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1d534-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d534-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d534-115">Requirements</span></span>  
 <span data-ttu-id="1d534-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d534-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d534-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d534-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d534-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d534-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d534-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d534-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d534-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d534-120">See also</span></span>
- [<span data-ttu-id="1d534-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d534-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1d534-122">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d534-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
