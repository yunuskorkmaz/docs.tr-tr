---
title: ICorProfilerFunctionControl::SetCodegenFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43c32d1ce4f804da8980dc0c566a77e5b076661b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459619"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="6f1d4-102">ICorProfilerFunctionControl::SetCodegenFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f1d4-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="6f1d4-103">Bir veya daha fazla bayraklarını ayarlar [cor_prf_codegen_flags sabit](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) denetim kod oluşturma için bir tam zamanında (JIT) numaralandırma işlevi yeniden derlenebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f1d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f1d4-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f1d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f1d4-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="6f1d4-106">[in] Bir veya daha fazla bayraklarını [cor_prf_codegen_flags sabit](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f1d4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f1d4-107">Remarks</span></span>  
 <span data-ttu-id="6f1d4-108">Profil Oluşturucu bu arabirimi aracılığıyla örneği alır [Icorprofilercallback4::getrejıtparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="6f1d4-109">`SetCodegenFlags` derlenmiş işlevi için kod oluşturmanın denetlemek profil oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="6f1d4-110">Tüm diğer JIT derleme parametrelerle birlikte gibi kod oluşturma bayrakları işlevi tüm örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="6f1d4-111">JIT Derleyici bir işlev derlenirken başka bir kaynak tarafından belirtilen diğer bayraklar yanı sıra bu Derleme bayrakları göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="6f1d4-112">Hata ayıklayıcı diğer kaynaklar dahil, Profil Oluşturucu tarafından başlangıçta tarafından belirlenen kullanarak genel bayraklar [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi (değerlerle `COR_PRF_DISABLE_INLINING` ve `COR_PRF_DISABLE_OPTIMIZATIONS`) ve profil oluşturucu 's [ Icorprofilercallback::jıtınlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="6f1d4-113">JIT Derleyici istekleri en iyi duruma getirme, en az bir kaynak için öncelik verir.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="6f1d4-114">Örneğin, profil oluşturucu belirtiyorsa `COR_PRF_DISABLE_INLINING` başlangıçta, belirtmediği ancak `COR_PRF_CODEGEN_DISABLE_INLINING` içinde [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) geri arama, satır içi kullanım hala devre dışı.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="6f1d4-115">Benzer şekilde, profil oluşturucu belirttiğini `COR_PRF_CODEGEN_DISABLE_INLINING` içinde `SetCodegenFlags`, ancak sonra devre dışı bırakır kullanarak satır içi kullanım [Icorprofilercallback::jıtınlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) geri arama, satır içi kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f1d4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f1d4-116">Requirements</span></span>  
 <span data-ttu-id="6f1d4-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f1d4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f1d4-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f1d4-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f1d4-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f1d4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f1d4-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f1d4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1d4-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f1d4-121">See Also</span></span>  
 [<span data-ttu-id="6f1d4-122">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f1d4-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
