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
ms.openlocfilehash: 75414ec3d2b30fe8afc5db1e97c81f34b29a3115
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864680"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="32b5d-102">ICorProfilerFunctionControl::SetCodegenFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32b5d-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="32b5d-103">Tam zamanında (JıT) yeniden derleme işlevine kod oluşturmayı denetlemek için [cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="32b5d-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32b5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32b5d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32b5d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32b5d-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="32b5d-106">'ndaki [Cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak.</span><span class="sxs-lookup"><span data-stu-id="32b5d-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32b5d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32b5d-107">Remarks</span></span>  
 <span data-ttu-id="32b5d-108">Profiler, [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="32b5d-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="32b5d-109">`SetCodegenFlags`, profil oluşturucunun yeniden derlenmiş işlev için kod oluşturmayı denetlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="32b5d-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="32b5d-110">Diğer tüm JıT yeniden derleme parametrelerinde olduğu gibi, kod oluşturma bayrakları işlevin tüm örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="32b5d-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="32b5d-111">JıT derleyicisi, bir işlev derlenirken diğer kaynaklar tarafından belirtilen diğer bayraklarla birlikte bu derleme bayraklarını dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="32b5d-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="32b5d-112">Diğer kaynaklar, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemi (`COR_PRF_DISABLE_INLINING` ve `COR_PRF_DISABLE_OPTIMIZATIONS`) ve profil oluşturucunun [ICorProfilerCallback:: jıntıl](icorprofilercallback-jitinlining-method.md) geri çağırması kullanılarak başlangıçta profil oluşturucu tarafından ayarlanan hata ayıklayıcıyı, genel bayrakları içerir.</span><span class="sxs-lookup"><span data-stu-id="32b5d-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="32b5d-113">JıT derleyicisi en az en iyileştirme miktarını isteyen bir kaynağa öncelik verir.</span><span class="sxs-lookup"><span data-stu-id="32b5d-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="32b5d-114">Örneğin, profil oluşturucu başlangıçta `COR_PRF_DISABLE_INLINING` belirtirse, ancak [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) geri aramasında `COR_PRF_CODEGEN_DISABLE_INLINING` belirtmezse, satır içi hala devre dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="32b5d-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="32b5d-115">Benzer şekilde, profil oluşturucu `SetCodegenFlags``COR_PRF_CODEGEN_DISABLE_INLINING` belirtmezse, ancak [ICorProfilerCallback:: jınkıx](icorprofilercallback-jitinlining-method.md) geri çağırma özelliğini kullanarak geçersiz kılma işlemini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="32b5d-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32b5d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32b5d-116">Requirements</span></span>  
 <span data-ttu-id="32b5d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b5d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32b5d-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="32b5d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32b5d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="32b5d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32b5d-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32b5d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b5d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32b5d-121">See also</span></span>

- [<span data-ttu-id="32b5d-122">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32b5d-122">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
