---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 yöntemi'
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
ms.openlocfilehash: 34f292d9bec4bcd334f824f7e3e1fd127331ba33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646978"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="bc042-103">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc042-103">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>

<span data-ttu-id="bc042-104">Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarının güncelleştirilmiş sürümlerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc042-104">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc042-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc042-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc042-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc042-106">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="bc042-107">'ndaki [FunctionEnter2](functionenter2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc042-107">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="bc042-108">'ndaki [FunctionLeave2](functionleave2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc042-108">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="bc042-109">'ndaki [FunctionTailcall2](functiontailcall2-function.md) geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc042-109">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc042-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc042-110">Remarks</span></span>  

 <span data-ttu-id="bc042-111">`SetEnterLeaveFunctionHooks2`Yöntemi [ICorProfilerInfo:: Setenterleavefunctionkancalar](icorprofilerinfo-setenterleavefunctionhooks-method.md) yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="bc042-111">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="bc042-112">ENTER/Leave/bir çağrı geri çağırmaların daha yeni sürümleri olarak kullanılacak işlevleri belirtmek için, önceki ' ni kullanın ve ENTER/Leave/, çağrı geri çağırmaların eski sürümleri olarak kullanılacak işlevleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="bc042-112">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="bc042-113">Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc042-113">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="bc042-114">Bu nedenle, bir profil oluşturucu hem hem de çağırır `ICorProfilerInfo::SetEnterLeaveFunctionHooks` `SetEnterLeaveFunctionHooks2` , `SetEnterLeaveFunctionHooks2` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc042-114">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="bc042-115">`SetEnterLeaveFunctionHooks2`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc042-115">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc042-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc042-116">Requirements</span></span>  

 <span data-ttu-id="bc042-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc042-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc042-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bc042-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc042-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bc042-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc042-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc042-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc042-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc042-121">See also</span></span>

- [<span data-ttu-id="bc042-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc042-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="bc042-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc042-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
