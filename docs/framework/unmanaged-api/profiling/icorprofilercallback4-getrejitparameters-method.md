---
title: ICorProfilerCallback4::GetReJITParameters Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.GetReJITParameters
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: acecbe10fd79394b27e6264c337d584d9fb259b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="3894c-102">ICorProfilerCallback4::GetReJITParameters Metodu</span><span class="sxs-lookup"><span data-stu-id="3894c-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="3894c-103">Yeni bir derlenmiş yöntem gövdesi için başka bir kod oluşturma bayrakları ayarlamak Kod Oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="3894c-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3894c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3894c-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3894c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3894c-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="3894c-106">[in] JIT derleme parametreleri için CLR gerekiyor yöntemi içeren modülü.</span><span class="sxs-lookup"><span data-stu-id="3894c-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="3894c-107">[in] `MethodDef` CLR gereken JIT derleme parametreleri yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3894c-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="3894c-108">[in] Bir işaretçi bir [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) profil oluşturucu yeniden derlenmesi yöntemi JIT derleme bilgilerini sağlamak için kullanabileceğiniz arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3894c-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3894c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3894c-109">Remarks</span></span>  
 <span data-ttu-id="3894c-110">CLR sorunları bir `GetReJITParameters` geri çağırma böylece profil oluşturucu belirli bir yöntemin yeniden derlenmesi için parametreleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3894c-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="3894c-111">`GetReJITParameters` Geri çağırma işlevi yalnızca bir kez verildiği; bu işlev tüm örneklerini Profil Oluşturucu tarafından sağlanan parametreleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3894c-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3894c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3894c-112">Requirements</span></span>  
 <span data-ttu-id="3894c-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3894c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3894c-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3894c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3894c-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3894c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3894c-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3894c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3894c-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3894c-117">See Also</span></span>  
 [<span data-ttu-id="3894c-118">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="3894c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3894c-119">Icorprofilercallback4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3894c-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="3894c-120">Jıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="3894c-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="3894c-121">Rejıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="3894c-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
