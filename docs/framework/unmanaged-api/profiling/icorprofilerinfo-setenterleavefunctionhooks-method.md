---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2d45e98f3e7b71375b14c43c4bff4929bc79494
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142538"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="79752-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79752-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="79752-103">Profil Oluşturucu uygulanan işlevleri "enter", "Ayrıl" ve "tailcall" hooks yönetilen işlevlerin çağrılmasına belirtir.</span><span class="sxs-lookup"><span data-stu-id="79752-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79752-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79752-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79752-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79752-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="79752-106">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="79752-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="79752-107">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="79752-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="79752-108">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="79752-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79752-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79752-109">Remarks</span></span>  
 <span data-ttu-id="79752-110">.NET Framework sürüm 1.0, her işlev işaretçisi, karşılık gelen bir geri çağırma devre dışı bırakmak için null olabilir.</span><span class="sxs-lookup"><span data-stu-id="79752-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="79752-111">Bir kerede yalnızca bir dizi geri çağırmaları etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="79752-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="79752-112">Bu nedenle, her ikisi de bir profil oluşturucu çağırırsa `SetEnterLeaveFunctionHooks` ve [Icorprofilerınfo2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), ardından `SetEnterLeaveFunctionHooks2` önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="79752-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="79752-113">`SetEnterLeaveFunctionHooks` Yöntemi yalnızca profil oluşturucu çağrılabilir [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="79752-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79752-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79752-114">Requirements</span></span>  
 <span data-ttu-id="79752-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79752-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79752-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79752-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79752-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79752-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79752-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79752-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79752-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79752-119">See also</span></span>

- [<span data-ttu-id="79752-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79752-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
