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
ms.openlocfilehash: 2c06b9b7933245dc0e69e430a3fe4a515f8a50f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449584"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="67a14-102">ICorProfilerInfo3::SetFunctionIDMapper2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67a14-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="67a14-103">Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen `FunctionID` değerlerini alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="67a14-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="67a14-104">Bu yöntem, [ICorProfilerInfo:: SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) yöntemini ek bir veri parametresiyle genişletir. Bu, profil oluşturucular çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="67a14-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a14-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67a14-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67a14-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67a14-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="67a14-107">'ndaki `FunctionID` değerlerini alternatif değerleriyle eşlemek için çağrılacak bir [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) uygulamasına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67a14-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="67a14-108">'ndaki Geçerli çalışma zamanı tarafından yapılan her [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) işlev çağrısına geçirilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67a14-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="67a14-109">Profil Oluşturucu bu bilgileri çalışma zamanları arasından ayırt etmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="67a14-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67a14-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="67a14-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67a14-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67a14-111">Remarks</span></span>  
 <span data-ttu-id="67a14-112">FunctionID değerleri için alternatifler, profil oluşturucunun işlev giriş/çıkış kancalarına ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); veya [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) veya [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) yöntemiyle belirtilen şekilde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="67a14-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="67a14-113">`FunctionIDMapper2` yöntemi yalnızca bir kez ayarlanabilir; Bunu [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırması içinde ayarlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="67a14-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a14-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67a14-114">Requirements</span></span>  
 <span data-ttu-id="67a14-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a14-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a14-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="67a14-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67a14-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="67a14-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67a14-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a14-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a14-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67a14-119">See also</span></span>

- [<span data-ttu-id="67a14-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="67a14-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="67a14-121">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67a14-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="67a14-122">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="67a14-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="67a14-123">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67a14-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
