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
ms.openlocfilehash: 107f596801832809e64088c85540c441e66189cf
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868479"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="74844-102">ICorProfilerInfo3::SetFunctionIDMapper2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74844-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="74844-103">Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen `FunctionID` değerlerini alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="74844-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="74844-104">Bu yöntem, [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) yöntemini ek bir veri parametresiyle genişletir. Bu, profil oluşturucular çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="74844-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74844-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74844-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74844-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74844-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="74844-107">'ndaki `FunctionID` değerlerini alternatif değerleriyle eşlemek için çağrılacak bir [FunctionIDMapper2](functionidmapper2-function.md) uygulamasına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74844-107">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="74844-108">'ndaki Geçerli çalışma zamanı tarafından yapılan her [FunctionIDMapper2](functionidmapper2-function.md) işlev çağrısına geçirilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74844-108">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="74844-109">Profil Oluşturucu bu bilgileri çalışma zamanları arasından ayırt etmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="74844-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74844-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="74844-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74844-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74844-111">Remarks</span></span>  
 <span data-ttu-id="74844-112">FunctionID değerleri için alternatifler, profil oluşturucunun işlev giriş/çıkış kancalarına ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md); veya [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) veya [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) yöntemiyle belirtilen şekilde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="74844-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="74844-113">`FunctionIDMapper2` yöntemi yalnızca bir kez ayarlanabilir; Bunu [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırması içinde ayarlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="74844-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74844-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74844-114">Requirements</span></span>  
 <span data-ttu-id="74844-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74844-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74844-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74844-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74844-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74844-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74844-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74844-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74844-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74844-119">See also</span></span>

- [<span data-ttu-id="74844-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="74844-120">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="74844-121">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74844-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="74844-122">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74844-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="74844-123">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74844-123">Profiling</span></span>](index.md)
