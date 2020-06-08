---
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
ms.openlocfilehash: 177127c8c53e4fee31f7007d04c49cc337cca458
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498732"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="d8ce9-102">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8ce9-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="d8ce9-103">Bir kod profil oluşturucunun, belirli bir yöntemi yeniden oluştururken JıT derleyicisinin nasıl kod üretmelidir denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8ce9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d8ce9-104">Methods</span></span>  
  
|<span data-ttu-id="d8ce9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d8ce9-105">Method</span></span>|<span data-ttu-id="d8ce9-106">Description</span><span class="sxs-lookup"><span data-stu-id="d8ce9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8ce9-107">SetCodegenFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ce9-107">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="d8ce9-108">Tam zamanında (JıT) yeniden derleme işlevine kod oluşturmayı denetlemek için [cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="d8ce9-109">SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ce9-109">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="d8ce9-110">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="d8ce9-111">SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ce9-111">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="d8ce9-112">Belirtilen ortak ara dil (CıL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8ce9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ce9-113">Remarks</span></span>  
 <span data-ttu-id="d8ce9-114">`ICorProfilerFunctionControl`Arabirimi, tek bir yeniden derlenmiş işlev için kod oluşturmayı denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="d8ce9-115">Profiler, [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="d8ce9-116">Her bir örneği `ICorProfilerFunctionControl` bir işlevin tüm örneklerini denetler.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ce9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8ce9-117">Requirements</span></span>  
 <span data-ttu-id="d8ce9-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ce9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ce9-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d8ce9-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8ce9-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8ce9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ce9-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ce9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ce9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ce9-122">See also</span></span>

- [<span data-ttu-id="d8ce9-123">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8ce9-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d8ce9-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d8ce9-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d8ce9-125">EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ce9-125">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
