---
title: ICorProfilerInfo::SetFunctionIDMapper Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 4ba3c378b93e3ae1ef288c0edabfacfcfd7070d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438668"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="d0d2a-102">ICorProfilerInfo::SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0d2a-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="d0d2a-103">Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen `FunctionID` değerlerini alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0d2a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0d2a-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="d0d2a-106">'ndaki `FunctionID` değerlerini alternatif değerleriyle eşlemek için çağrılacak [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) uygulamasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0d2a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0d2a-107">Remarks</span></span>  
 <span data-ttu-id="d0d2a-108">`FunctionID` değerler için alternatifler, " [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) yöntemi tarafından belirtilen Profiler 'ın işlev girdisine/çıkış kancalarına ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="d0d2a-109">`FunctionIDMapper` yalnızca bir kez ayarlanabilir ve bunu [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırması içinde ayarlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d2a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0d2a-110">Requirements</span></span>  
 <span data-ttu-id="d0d2a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0d2a-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d0d2a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0d2a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d0d2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0d2a-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d2a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-115">See also</span></span>

- [<span data-ttu-id="d0d2a-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0d2a-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
