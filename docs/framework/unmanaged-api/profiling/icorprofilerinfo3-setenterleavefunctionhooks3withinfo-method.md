---
title: "ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9d9af004abbee19d6b553c431381af55d210095
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="e39ac-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e39ac-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="e39ac-103">Üzerinde adlı profil oluşturucu uygulanan işlevler belirtir [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) Yönetilen işlevler kancaları.</span><span class="sxs-lookup"><span data-stu-id="e39ac-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e39ac-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e39ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e39ac-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="e39ac-106">[in] Bir işaretçi olarak kullanılacak uygulama `FunctionEnter3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e39ac-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="e39ac-107">[in] Bir işaretçi olarak kullanılacak uygulama `FunctionLeave3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e39ac-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="e39ac-108">[in] Bir işaretçi olarak kullanılacak uygulama `FunctionTailcall3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e39ac-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e39ac-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e39ac-109">Remarks</span></span>  
 <span data-ttu-id="e39ac-110">[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) kancalar yığın çerçevesi ve bağımsız değişkeni denetleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39ac-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="e39ac-111">Bu bilgilere erişmek üzere `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayrakları ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e39ac-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="e39ac-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve sonra kullanmak için yöntemi `SetEnterLeaveFunctionHooks3WithInfo` uygulamanız bu işlevin kaydetmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="e39ac-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="e39ac-113">Geri aramalar yalnızca bir dizi aynı anda etkin olabilir ve en yeni sürüme önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="e39ac-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="e39ac-114">Bu nedenle, bir profil oluşturucu her ikisi de çağırırsa [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) ve `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e39ac-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="e39ac-115">`SetEnterLeaveFunctionHooks3WithInfo` Yöntemi yalnızca profil oluşturucu 's adlı [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e39ac-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e39ac-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e39ac-116">Requirements</span></span>  
 <span data-ttu-id="e39ac-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e39ac-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e39ac-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e39ac-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e39ac-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e39ac-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e39ac-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e39ac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39ac-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e39ac-121">See Also</span></span>  
 [<span data-ttu-id="e39ac-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="e39ac-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="e39ac-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="e39ac-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="e39ac-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="e39ac-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="e39ac-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="e39ac-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="e39ac-126">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="e39ac-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="e39ac-127">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="e39ac-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="e39ac-128">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="e39ac-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="e39ac-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e39ac-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="e39ac-130">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e39ac-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="e39ac-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e39ac-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e39ac-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e39ac-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
