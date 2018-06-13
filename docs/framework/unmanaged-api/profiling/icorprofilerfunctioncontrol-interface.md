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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0daf772702ada9d426b3da6913fff0186e33564
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455657"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="376e2-102">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="376e2-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="376e2-103">Ortak dil çalışma zamanı ile nasıl JIT Derleyici kodu belirli bir yöntemi yeniden derlenmesi sırasında oluşturulmasına denetlemek için (CLR) iletişim kurmak bir kod profil oluşturucu izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="376e2-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="376e2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="376e2-104">Methods</span></span>  
  
|<span data-ttu-id="376e2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="376e2-105">Method</span></span>|<span data-ttu-id="376e2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="376e2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="376e2-107">SetCodegenFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="376e2-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="376e2-108">Bir veya daha fazla bayraklarını ayarlar [cor_prf_codegen_flags sabit](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) denetim kod oluşturma için bir tam zamanında (JIT) numaralandırma işlevi yeniden derlenebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="376e2-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="376e2-109">SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="376e2-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="376e2-110">Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="376e2-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="376e2-111">SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="376e2-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="376e2-112">Kod Haritası belirtilen işlev için belirtilen ortak Ara dili (CIL) eşleme girdilerini kullanarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="376e2-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="376e2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="376e2-113">Remarks</span></span>  
 <span data-ttu-id="376e2-114">`ICorProfilerFunctionControl` Arabirimi kod oluşturma için tek bir derlenmiş işlevi denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="376e2-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="376e2-115">Profil Oluşturucu bu arabirimi aracılığıyla örneği alır [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="376e2-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="376e2-116">Her örneği `ICorProfilerFunctionControl` bir işlev tüm örneklerini denetler.</span><span class="sxs-lookup"><span data-stu-id="376e2-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="376e2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="376e2-117">Requirements</span></span>  
 <span data-ttu-id="376e2-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="376e2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="376e2-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="376e2-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="376e2-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="376e2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="376e2-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="376e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="376e2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="376e2-122">See Also</span></span>  
 [<span data-ttu-id="376e2-123">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="376e2-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="376e2-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="376e2-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="376e2-125">EnumJITedFunctions2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="376e2-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
