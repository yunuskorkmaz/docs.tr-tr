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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73321a28b1c61775d08e2c60ee2b9a863b8250dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121686"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="fb367-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb367-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="fb367-103">Üzerinde çağrılır profil oluşturucu uygulanan işlevleri belirtir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="fb367-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb367-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb367-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb367-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb367-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="fb367-106">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya `FunctionEnter3` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fb367-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="fb367-107">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya `FunctionLeave3` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fb367-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="fb367-108">[in] Bir işaretçi olarak kullanılmak üzere uygulamaya `FunctionTailcall3` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fb367-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb367-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb367-109">Remarks</span></span>  
 <span data-ttu-id="fb367-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) kancaları yığın çerçeve ve bağımsız değişken İnceleme sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fb367-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="fb367-111">Bu bilgilere erişmek üzere `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayrakları ayarlanmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="fb367-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="fb367-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve ardından yöntemi [Icorprofilerınfo3::setenterleavefunctionhooks3withınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) yöntemi kaydetmek için Bu işlev uygulaması.</span><span class="sxs-lookup"><span data-stu-id="fb367-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="fb367-113">Bir kerede yalnızca bir dizi geri çağırmaları etkin olabilir ve en yeni sürümü önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="fb367-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="fb367-114">Bu nedenle, her ikisi de bir profil oluşturucu çağırırsa [SetEnterLeaveFunctionHooks2 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) ve `SetEnterLeaveFunctionHooks3` yöntemi `SetEnterLeaveFunctionHooks3` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb367-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="fb367-115">`SetEnterLeaveFunctionHooks3` Yöntemi yalnızca profil oluşturucuyu 's adlı [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fb367-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb367-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb367-116">Requirements</span></span>  
 <span data-ttu-id="fb367-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb367-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb367-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb367-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb367-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb367-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb367-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb367-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb367-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb367-121">See also</span></span>

- [<span data-ttu-id="fb367-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fb367-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="fb367-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="fb367-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="fb367-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="fb367-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="fb367-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="fb367-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="fb367-126">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="fb367-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="fb367-127">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="fb367-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="fb367-128">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="fb367-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="fb367-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fb367-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="fb367-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="fb367-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fb367-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fb367-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fb367-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fb367-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
