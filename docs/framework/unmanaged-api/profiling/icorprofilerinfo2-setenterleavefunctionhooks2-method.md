---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bea9be4db2730a67485ef9a504bbc69c096e76c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="3c6f5-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c6f5-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="3c6f5-103">Profil Oluşturucu uygulanan işlevler "girin", "bırakın" ve "tailcall" kancaları yönetilen işlevlerin güncelleştirilmiş sürümlerinde çağrılacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c6f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c6f5-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c6f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c6f5-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="3c6f5-106">[in] Bir işaretçi olarak kullanılacak uygulama [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="3c6f5-107">[in] Bir işaretçi olarak kullanılacak uygulama [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="3c6f5-108">[in] Bir işaretçi olarak kullanılacak uygulama [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c6f5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c6f5-109">Remarks</span></span>  
 <span data-ttu-id="3c6f5-110">`SetEnterLeaveFunctionHooks2` Yöntemi benzer [Icorprofilerınfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="3c6f5-111">Önceki bırakın/enter/tailcall geri aramalar eski sürümleri kullanılacak işlevleri belirtmek için daha yeni sürümleri bırakın/enter/tailcall geri aramalar ve ikinci kullanılacak işlevleri belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="3c6f5-112">Geri aramalar yalnızca bir dizi aynı anda etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="3c6f5-113">Bu nedenle, bir profil oluşturucu her ikisi de çağırırsa `ICorProfilerInfo::SetEnterLeaveFunctionHooks` ve `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="3c6f5-114">`SetEnterLeaveFunctionHooks2` Yöntemi yalnızca profil oluşturucu 's adlı [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c6f5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c6f5-115">Requirements</span></span>  
 <span data-ttu-id="3c6f5-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c6f5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c6f5-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c6f5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c6f5-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c6f5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c6f5-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c6f5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6f5-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c6f5-120">See Also</span></span>  
 [<span data-ttu-id="3c6f5-121">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c6f5-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3c6f5-122">Icorprofilerınfo2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c6f5-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
