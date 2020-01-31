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
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868596"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="2c523-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c523-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="2c523-103">Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarının güncelleştirilmiş sürümlerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c523-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c523-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c523-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c523-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c523-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="2c523-106">'ndaki [FunctionEnter2](functionenter2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c523-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="2c523-107">'ndaki [FunctionLeave2](functionleave2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c523-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="2c523-108">'ndaki [FunctionTailcall2](functiontailcall2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c523-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c523-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c523-109">Remarks</span></span>  
 <span data-ttu-id="2c523-110">`SetEnterLeaveFunctionHooks2` yöntemi [ICorProfilerInfo:: Setenterleavefunctionkancalar](icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="2c523-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="2c523-111">ENTER/Leave/bir çağrı geri çağırmaların daha yeni sürümleri olarak kullanılacak işlevleri belirtmek için, önceki ' ni kullanın ve ENTER/Leave/, çağrı geri çağırmaların eski sürümleri olarak kullanılacak işlevleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="2c523-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="2c523-112">Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c523-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="2c523-113">Bu nedenle, bir profil oluşturucu hem `ICorProfilerInfo::SetEnterLeaveFunctionHooks` hem de `SetEnterLeaveFunctionHooks2`çağırırsa `SetEnterLeaveFunctionHooks2` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c523-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="2c523-114">`SetEnterLeaveFunctionHooks2` yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c523-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c523-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c523-115">Requirements</span></span>  
 <span data-ttu-id="2c523-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c523-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c523-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2c523-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c523-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c523-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c523-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c523-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c523-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c523-120">See also</span></span>

- [<span data-ttu-id="2c523-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c523-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2c523-122">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c523-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
