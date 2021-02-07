---
description: ': ICorProfilerFunctionControl arabirimi hakkında daha fazla bilgi edinin'
title: ICorProfilerFunctionControl Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 7b4ac58d2b8754108b4e10493596776987a93a49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753321"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="fe4c9-103">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe4c9-103">ICorProfilerFunctionControl Interface</span></span>

<span data-ttu-id="fe4c9-104">Bir kod profil oluşturucunun, belirli bir yöntemi yeniden oluştururken JıT derleyicisinin nasıl kod üretmelidir denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-104">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe4c9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fe4c9-105">Methods</span></span>  
  
|<span data-ttu-id="fe4c9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe4c9-106">Method</span></span>|<span data-ttu-id="fe4c9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe4c9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe4c9-108">SetCodegenFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4c9-108">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="fe4c9-109">Tam zamanında (JıT) yeniden derleme işlevine kod oluşturmayı denetlemek için [cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-109">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="fe4c9-110">SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4c9-110">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="fe4c9-111">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-111">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="fe4c9-112">SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4c9-112">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="fe4c9-113">Belirtilen ortak ara dil (CıL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-113">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe4c9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe4c9-114">Remarks</span></span>  

 <span data-ttu-id="fe4c9-115">`ICorProfilerFunctionControl`Arabirimi, tek bir yeniden derlenmiş işlev için kod oluşturmayı denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-115">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="fe4c9-116">Profiler, [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-116">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="fe4c9-117">Her bir örneği `ICorProfilerFunctionControl` bir işlevin tüm örneklerini denetler.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-117">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe4c9-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe4c9-118">Requirements</span></span>  

 <span data-ttu-id="fe4c9-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe4c9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe4c9-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fe4c9-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe4c9-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe4c9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe4c9-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe4c9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4c9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe4c9-123">See also</span></span>

- [<span data-ttu-id="fe4c9-124">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe4c9-124">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="fe4c9-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe4c9-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="fe4c9-126">EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe4c9-126">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
