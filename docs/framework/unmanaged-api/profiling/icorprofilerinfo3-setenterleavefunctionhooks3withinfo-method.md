---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: 4fe18b4f07e6f282571b13faff5ce51b66ce416b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868492"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="1b955-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b955-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="1b955-103">Yönetilen işlevlerin [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) kancaları üzerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b955-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b955-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b955-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b955-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b955-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="1b955-106">'ndaki `FunctionEnter3WithInfo` geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1b955-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="1b955-107">'ndaki `FunctionLeave3WithInfo` geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1b955-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="1b955-108">'ndaki `FunctionTailcall3WithInfo` geri çağırması olarak kullanılacak uygulamaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1b955-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b955-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b955-109">Remarks</span></span>  
 <span data-ttu-id="1b955-110">[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) kancaları yığın çerçevesi ve bağımsız değişken incelemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b955-110">The [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="1b955-111">Bu bilgilere erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayraklarının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b955-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="1b955-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için `SetEnterLeaveFunctionHooks3WithInfo` yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1b955-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="1b955-113">Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir ve en yeni sürüm öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="1b955-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="1b955-114">Bu nedenle, bir profil oluşturucu hem [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) hem de `SetEnterLeaveFunctionHooks3WithInfo`çağırırsa, `SetEnterLeaveFunctionHooks3WithInfo` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b955-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="1b955-115">`SetEnterLeaveFunctionHooks3WithInfo` yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b955-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b955-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b955-116">Requirements</span></span>  
 <span data-ttu-id="1b955-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b955-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b955-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1b955-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b955-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1b955-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b955-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b955-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b955-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b955-121">See also</span></span>

- [<span data-ttu-id="1b955-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="1b955-122">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="1b955-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="1b955-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="1b955-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="1b955-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="1b955-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="1b955-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="1b955-126">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="1b955-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="1b955-127">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="1b955-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="1b955-128">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="1b955-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="1b955-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1b955-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="1b955-130">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b955-130">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1b955-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b955-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1b955-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b955-132">Profiling</span></span>](index.md)
