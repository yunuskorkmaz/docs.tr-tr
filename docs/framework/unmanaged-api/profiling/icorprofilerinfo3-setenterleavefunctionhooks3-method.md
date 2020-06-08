---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: eb658d682ce589b7dfdcfc0228d0c657310e6f7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496275"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="fe932-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe932-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="fe932-103">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md) işlevlerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe932-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe932-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe932-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe932-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe932-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="fe932-106">'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionEnter3` .</span><span class="sxs-lookup"><span data-stu-id="fe932-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="fe932-107">'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionLeave3` .</span><span class="sxs-lookup"><span data-stu-id="fe932-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="fe932-108">'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionTailcall3` .</span><span class="sxs-lookup"><span data-stu-id="fe932-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe932-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe932-109">Remarks</span></span>  
 <span data-ttu-id="fe932-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md) kancaları yığın çerçevesi ve bağımsız değişken incelemesi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fe932-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="fe932-111">Bu bilgilere erişmek için,, `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayraklarının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe932-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="fe932-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metodunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe932-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="fe932-113">Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir ve en yeni sürüm öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="fe932-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="fe932-114">Bu nedenle, bir profil oluşturucu hem [SetEnterLeaveFunctionHooks2 yöntemini](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) hem de `SetEnterLeaveFunctionHooks3` yöntemini çağırırsa, `SetEnterLeaveFunctionHooks3` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe932-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="fe932-115">`SetEnterLeaveFunctionHooks3`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe932-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe932-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe932-116">Requirements</span></span>  
 <span data-ttu-id="fe932-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe932-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe932-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fe932-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe932-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe932-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe932-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe932-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe932-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe932-121">See also</span></span>

- [<span data-ttu-id="fe932-122">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="fe932-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="fe932-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="fe932-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="fe932-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="fe932-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="fe932-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="fe932-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="fe932-126">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="fe932-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="fe932-127">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="fe932-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="fe932-128">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="fe932-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="fe932-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fe932-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="fe932-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="fe932-130">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fe932-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe932-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="fe932-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe932-132">Profiling</span></span>](index.md)
