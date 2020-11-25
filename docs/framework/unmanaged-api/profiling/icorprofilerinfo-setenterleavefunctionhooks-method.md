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
ms.openlocfilehash: 18aed5c5314fc1057767b599c538952a1d4d6b57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722238"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="ec1ef-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec1ef-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>

<span data-ttu-id="ec1ef-103">Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarında çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec1ef-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ec1ef-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec1ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec1ef-105">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="ec1ef-106">'ndaki [FunctionEnter](functionenter-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="ec1ef-107">'ndaki [FunctionLeave](functionleave-function.md) geri araması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="ec1ef-108">'ndaki [Functionsemblycall](functiontailcall-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec1ef-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec1ef-109">Remarks</span></span>  

 <span data-ttu-id="ec1ef-110">.NET Framework sürüm 1,0 ' de, her işlev işaretçisi ilgili geri çağırma işlemini devre dışı bırakmak için null olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="ec1ef-111">Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="ec1ef-112">Bu nedenle, bir profil oluşturucu hem hem de `SetEnterLeaveFunctionHooks` [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)' ı çağırırsa, `SetEnterLeaveFunctionHooks2` öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="ec1ef-113">`SetEnterLeaveFunctionHooks`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec1ef-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec1ef-114">Requirements</span></span>  

 <span data-ttu-id="ec1ef-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec1ef-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec1ef-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ec1ef-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec1ef-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ec1ef-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec1ef-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec1ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1ef-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec1ef-119">See also</span></span>

- [<span data-ttu-id="ec1ef-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec1ef-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
