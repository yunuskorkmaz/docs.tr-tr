---
description: ': ICorProfilerFunctionControl:: SetCodegenFlags yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 61fa8be0993a06a3b2d352af408ac47b7b30e385
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781629"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="5a52b-103">ICorProfilerFunctionControl::SetCodegenFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a52b-103">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>

<span data-ttu-id="5a52b-104">Tam zamanında (JıT) yeniden derleme işlevine kod oluşturmayı denetlemek için [cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5a52b-104">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a52b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a52b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a52b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a52b-106">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="5a52b-107">'ndaki [Cor_prf_codegen_flags](cor-prf-codegen-flags-enumeration.md) numaralandırmasından bir veya daha fazla bayrak.</span><span class="sxs-lookup"><span data-stu-id="5a52b-107">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a52b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a52b-108">Remarks</span></span>  

 <span data-ttu-id="5a52b-109">Profiler, [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) geri çağırması aracılığıyla bu arabirimin bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="5a52b-109">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="5a52b-110">`SetCodegenFlags` profil oluşturucunun, yeniden derlenmiş işlev için kod oluşturmayı denetlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5a52b-110">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="5a52b-111">Diğer tüm JıT yeniden derleme parametrelerinde olduğu gibi, kod oluşturma bayrakları işlevin tüm örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5a52b-111">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="5a52b-112">JıT derleyicisi, bir işlev derlenirken diğer kaynaklar tarafından belirtilen diğer bayraklarla birlikte bu derleme bayraklarını dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="5a52b-112">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="5a52b-113">Diğer kaynaklar, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini (değerleri `COR_PRF_DISABLE_INLINING` ve `COR_PRF_DISABLE_OPTIMIZATIONS` ) ve profil oluşturucunun [ICorProfilerCallback:: jınkıx](icorprofilercallback-jitinlining-method.md) geri aramasını kullanarak başlangıçta profil oluşturucu tarafından ayarlanan hata ayıklayıcıyı, genel bayrakları içerir.</span><span class="sxs-lookup"><span data-stu-id="5a52b-113">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="5a52b-114">JıT derleyicisi en az en iyileştirme miktarını isteyen bir kaynağa öncelik verir.</span><span class="sxs-lookup"><span data-stu-id="5a52b-114">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="5a52b-115">Örneğin, profil oluşturucu `COR_PRF_DISABLE_INLINING` Başlangıçta belirtiyorsa, ancak `COR_PRF_CODEGEN_DISABLE_INLINING` [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) geri çağırma öğesinde belirtilmemişse, hala devre dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a52b-115">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="5a52b-116">Benzer şekilde, profil oluşturucu `COR_PRF_CODEGEN_DISABLE_INLINING` içinde belirtilmemişse `SetCodegenFlags` , ancak [ICorProfilerCallback:: jıntıl](icorprofilercallback-jitinlining-method.md) geri aramasını kullanarak içe/veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5a52b-116">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a52b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a52b-117">Requirements</span></span>  

 <span data-ttu-id="5a52b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a52b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a52b-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5a52b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a52b-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5a52b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a52b-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a52b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a52b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a52b-122">See also</span></span>

- [<span data-ttu-id="5a52b-123">ICorProfilerFunctionControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a52b-123">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
