---
description: ': ICorProfilerCallback4:: Getrejparameters yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f8dbf2c6ae80e41b8427fdaf0ef617a83138bb14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788767"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="8b2c0-103">ICorProfilerCallback4::GetReJITParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-103">ICorProfilerCallback4::GetReJITParameters Method</span></span>

<span data-ttu-id="8b2c0-104">Kod Profilcisi yeni bir yeniden derlenmiş Yöntem gövdesi için alternatif kod oluşturma bayrakları ayarlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-104">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b2c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b2c0-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="8b2c0-107">'ndaki CLR 'nin JıT yeniden derleme parametrelerine ihtiyacı olan yöntemini içeren modül.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-107">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="8b2c0-108">'ndaki `MethodDef` Clr 'nın JIT yeniden derleme parametrelerine ihtiyacı olan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-108">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="8b2c0-109">'ndaki Profiler 'ın yeniden Derlenmekte olan yönteme yönelik JıT yeniden derleme bilgileri sağlamak için kullanabileceği [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-109">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b2c0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b2c0-110">Remarks</span></span>  

 <span data-ttu-id="8b2c0-111">CLR, `GetReJITParameters` profil oluşturucunun belirli bir yöntemi yeniden derleme parametrelerini belirleyebilmesi için bir geri çağırma işlemini yayınlar.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-111">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="8b2c0-112">`GetReJITParameters`Geri çağırma, işlev başına yalnızca bir kez verilir; profil oluşturucu tarafından sağlanan parametreler, bu işlevin tüm örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-112">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b2c0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b2c0-113">Requirements</span></span>  

 <span data-ttu-id="8b2c0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b2c0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b2c0-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8b2c0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b2c0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8b2c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b2c0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b2c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2c0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-118">See also</span></span>

- [<span data-ttu-id="8b2c0-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8b2c0-120">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-120">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="8b2c0-121">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-121">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="8b2c0-122">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-122">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
