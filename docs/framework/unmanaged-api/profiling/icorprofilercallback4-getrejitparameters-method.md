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
ms.openlocfilehash: 858d65783515a89a434cf719ef9d5a999643094c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865330"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="a7981-102">ICorProfilerCallback4::GetReJITParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7981-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="a7981-103">Kod Profilcisi yeni bir yeniden derlenmiş Yöntem gövdesi için alternatif kod oluşturma bayrakları ayarlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a7981-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7981-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7981-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7981-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7981-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a7981-106">'ndaki CLR 'nin JıT yeniden derleme parametrelerine ihtiyacı olan yöntemini içeren modül.</span><span class="sxs-lookup"><span data-stu-id="a7981-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="a7981-107">'ndaki CLR 'nin JıT yeniden derleme parametrelerine ihtiyacı olan metodun `MethodDef`.</span><span class="sxs-lookup"><span data-stu-id="a7981-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="a7981-108">'ndaki Profiler 'ın yeniden Derlenmekte olan yönteme yönelik JıT yeniden derleme bilgileri sağlamak için kullanabileceği [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7981-108">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7981-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7981-109">Remarks</span></span>  
 <span data-ttu-id="a7981-110">CLR, profil oluşturucunun belirli bir yöntemi yeniden derleme parametrelerini belirleyebilmesi için `GetReJITParameters` bir geri çağırma işlemini yayınlar.</span><span class="sxs-lookup"><span data-stu-id="a7981-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="a7981-111">`GetReJITParameters` geri çağırması her işlev için yalnızca bir kez verilir; Profil Oluşturucu tarafından sağlanan parametreler, bu işlevin tüm örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a7981-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7981-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7981-112">Requirements</span></span>  
 <span data-ttu-id="a7981-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7981-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7981-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7981-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7981-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7981-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7981-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7981-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7981-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7981-117">See also</span></span>

- [<span data-ttu-id="a7981-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7981-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a7981-119">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7981-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="a7981-120">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7981-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="a7981-121">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7981-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
