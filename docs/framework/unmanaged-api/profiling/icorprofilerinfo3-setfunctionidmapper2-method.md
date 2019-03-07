---
title: ICorProfilerInfo3::SetFunctionIDMapper2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee520ba95a8eefcc3322af0d0dd6e03c70d35cd4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468708"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="5285d-102">ICorProfilerInfo3::SetFunctionIDMapper2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5285d-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="5285d-103">Profil Oluşturucu uygulanan eşlemek için çağrılacak işlevi belirtir `FunctionID` değerleri oluşturucunun geçirilen alternatif, işlev girişi/çıkışı kancaları.</span><span class="sxs-lookup"><span data-stu-id="5285d-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="5285d-104">Bu yöntemin genişlettiği [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) profil Oluşturucular, çalışma zamanları arasındaki ayırt etmek için kullanabilir ve ek veri parametresi, yöntem.</span><span class="sxs-lookup"><span data-stu-id="5285d-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5285d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5285d-105">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5285d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5285d-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="5285d-107">[in] Bir işaretçi bir [Functionıdmapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) eşlemek için çağrılacak olan uygulama `FunctionID` alternatif değerlerine değerleri.</span><span class="sxs-lookup"><span data-stu-id="5285d-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="5285d-108">[in] Her geçirilir bir işaretçi [Functionıdmapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) işlev çağrısı geçerli çalışma zamanı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="5285d-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="5285d-109">Profil Oluşturucu, çalışma zamanları arasındaki belirsizliğini ortadan kaldırmak için bu bilgileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5285d-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5285d-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5285d-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5285d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5285d-111">Remarks</span></span>  
 <span data-ttu-id="5285d-112">Alternatifleri FunctionID değerleri için profil oluşturucunun işlev girişi/çıkışı kancaları için geçirilecek ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; veya [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) tarafından belirtilen [ SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) veya [Setenterleavefunctionhooks3withınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5285d-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="5285d-113">`FunctionIDMapper2` Yöntemi yalnızca bir kez ayarlanabilir; bu ayarladığınız öneririz [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="5285d-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5285d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5285d-114">Requirements</span></span>  
 <span data-ttu-id="5285d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5285d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5285d-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5285d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5285d-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5285d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5285d-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5285d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5285d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5285d-119">See also</span></span>
- [<span data-ttu-id="5285d-120">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="5285d-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="5285d-121">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5285d-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="5285d-122">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5285d-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5285d-123">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5285d-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
