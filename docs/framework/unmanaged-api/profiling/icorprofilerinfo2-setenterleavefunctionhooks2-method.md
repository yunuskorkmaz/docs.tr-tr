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
ms.openlocfilehash: 52988378ff4df0bb03e15c9a4b25efbcd6c318f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457732"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="35fd2-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35fd2-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="35fd2-103">Profil Oluşturucu uygulanan işlevler "girin", "bırakın" ve "tailcall" kancaları yönetilen işlevlerin güncelleştirilmiş sürümlerinde çağrılacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="35fd2-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35fd2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35fd2-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35fd2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35fd2-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="35fd2-106">[in] Bir işaretçi olarak kullanılacak uygulama [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="35fd2-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="35fd2-107">[in] Bir işaretçi olarak kullanılacak uygulama [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="35fd2-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="35fd2-108">[in] Bir işaretçi olarak kullanılacak uygulama [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="35fd2-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35fd2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35fd2-109">Remarks</span></span>  
 <span data-ttu-id="35fd2-110">`SetEnterLeaveFunctionHooks2` Yöntemi benzer [Icorprofilerınfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35fd2-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="35fd2-111">Önceki bırakın/enter/tailcall geri aramalar eski sürümleri kullanılacak işlevleri belirtmek için daha yeni sürümleri bırakın/enter/tailcall geri aramalar ve ikinci kullanılacak işlevleri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="35fd2-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="35fd2-112">Geri aramalar yalnızca bir dizi aynı anda etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="35fd2-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="35fd2-113">Bu nedenle, bir profil oluşturucu her ikisi de çağırırsa `ICorProfilerInfo::SetEnterLeaveFunctionHooks` ve `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35fd2-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="35fd2-114">`SetEnterLeaveFunctionHooks2` Yöntemi yalnızca profil oluşturucu 's adlı [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="35fd2-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35fd2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35fd2-115">Requirements</span></span>  
 <span data-ttu-id="35fd2-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35fd2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35fd2-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35fd2-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35fd2-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35fd2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35fd2-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35fd2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fd2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35fd2-120">See Also</span></span>  
 [<span data-ttu-id="35fd2-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35fd2-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="35fd2-122">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35fd2-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
