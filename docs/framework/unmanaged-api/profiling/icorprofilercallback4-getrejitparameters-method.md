---
title: ICorProfilerCallback4::GetReJITParameters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca176be93b92e44228d9b4063e87a62263e83e04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184879"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="13620-102">ICorProfilerCallback4::GetReJITParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13620-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="13620-103">Kod profil oluşturucu, yeni bir znovu yöntem gövdesi için başka bir kod oluşturma bayrakları ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="13620-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13620-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13620-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13620-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13620-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="13620-106">[in] Kendisi için CLR JIT yeniden derleme parametreleri gereken yöntemini içeren modül.</span><span class="sxs-lookup"><span data-stu-id="13620-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="13620-107">[in] `MethodDef` Yönteminin CLR JIT yeniden derleme parametreleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="13620-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="13620-108">[in] Bir işaretçi bir [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) profil oluşturucuyu yeniden derlenen yöntem JIT yeniden derleme bilgilerini sağlamak için kullanabileceğiniz arabirimi.</span><span class="sxs-lookup"><span data-stu-id="13620-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13620-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13620-109">Remarks</span></span>  
 <span data-ttu-id="13620-110">CLR sorunları bir `GetReJITParameters` geri çağırma profil oluşturucu, belirli bir yöntemin yeniden derlemeden parametrelerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13620-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="13620-111">`GetReJITParameters` Geri çağırma işlevi yalnızca bir kez verildiği; Profil Oluşturucu tarafından sağlanan parametreleri, bu işlevin tüm örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="13620-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13620-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13620-112">Requirements</span></span>  
 <span data-ttu-id="13620-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13620-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13620-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13620-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13620-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13620-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13620-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13620-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13620-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13620-117">See also</span></span>

- [<span data-ttu-id="13620-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13620-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="13620-119">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13620-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="13620-120">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13620-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="13620-121">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13620-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
