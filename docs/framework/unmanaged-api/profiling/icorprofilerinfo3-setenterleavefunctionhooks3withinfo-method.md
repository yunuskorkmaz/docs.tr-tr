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
ms.openlocfilehash: a30dde6f406cfb6d1140e7cd8e2a8f8f3ab40006
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="54a2c-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54a2c-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="54a2c-103">Üzerinde adlı profil oluşturucu uygulanan işlevler belirtir [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) Yönetilen işlevler kancaları.</span><span class="sxs-lookup"><span data-stu-id="54a2c-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54a2c-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54a2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54a2c-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="54a2c-106">[in] Bir işaretçi olarak kullanılacak uygulama `FunctionEnter3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="54a2c-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="54a2c-107">[in] Bir işaretçi olarak kullanılacak uygulama `FunctionLeave3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="54a2c-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="54a2c-108">[in] Bir işaretçi olarak kullanılacak uygulama `FunctionTailcall3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="54a2c-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54a2c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54a2c-109">Remarks</span></span>  
 <span data-ttu-id="54a2c-110">[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) kancalar yığın çerçevesi ve bağımsız değişkeni denetleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="54a2c-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="54a2c-111">Bu bilgilere erişmek üzere `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayrakları ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54a2c-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="54a2c-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve sonra kullanmak için yöntemi `SetEnterLeaveFunctionHooks3WithInfo` uygulamanız bu işlevin kaydetmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="54a2c-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="54a2c-113">Geri aramalar yalnızca bir dizi aynı anda etkin olabilir ve en yeni sürüme önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="54a2c-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="54a2c-114">Bu nedenle, bir profil oluşturucu her ikisi de çağırırsa [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) ve `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54a2c-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="54a2c-115">`SetEnterLeaveFunctionHooks3WithInfo` Yöntemi yalnızca profil oluşturucu 's adlı [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="54a2c-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54a2c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54a2c-116">Requirements</span></span>  
 <span data-ttu-id="54a2c-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54a2c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54a2c-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54a2c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54a2c-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54a2c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54a2c-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54a2c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a2c-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54a2c-121">See Also</span></span>  
 [<span data-ttu-id="54a2c-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="54a2c-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="54a2c-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="54a2c-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="54a2c-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="54a2c-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="54a2c-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="54a2c-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="54a2c-126">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="54a2c-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="54a2c-127">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="54a2c-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="54a2c-128">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="54a2c-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="54a2c-129">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="54a2c-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="54a2c-130">Icorprofilerınfo3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="54a2c-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="54a2c-131">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="54a2c-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="54a2c-132">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="54a2c-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
