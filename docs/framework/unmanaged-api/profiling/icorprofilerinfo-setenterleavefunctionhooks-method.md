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
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497458"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="bb680-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb680-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="bb680-103">Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarında çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb680-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb680-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bb680-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb680-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb680-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="bb680-106">'ndaki [FunctionEnter](functionenter-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb680-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="bb680-107">'ndaki [FunctionLeave](functionleave-function.md) geri araması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb680-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="bb680-108">'ndaki [Functionsemblycall](functiontailcall-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb680-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb680-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb680-109">Remarks</span></span>  
 <span data-ttu-id="bb680-110">.NET Framework sürüm 1,0 ' de, her işlev işaretçisi ilgili geri çağırma işlemini devre dışı bırakmak için null olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb680-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="bb680-111">Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb680-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="bb680-112">Bu nedenle, bir profil oluşturucu hem hem de `SetEnterLeaveFunctionHooks` [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)' ı çağırırsa, `SetEnterLeaveFunctionHooks2` öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="bb680-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="bb680-113">`SetEnterLeaveFunctionHooks`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb680-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb680-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb680-114">Requirements</span></span>  
 <span data-ttu-id="bb680-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb680-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb680-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bb680-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb680-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bb680-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb680-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb680-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb680-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb680-119">See also</span></span>

- [<span data-ttu-id="bb680-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb680-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
