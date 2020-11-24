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
ms.openlocfilehash: 3a9ab64730feaa372f9b5d9ad7cefcb86580ca5e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671180"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="9d4b5-102">ICorProfilerInfo::SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d4b5-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>

<span data-ttu-id="9d4b5-103">`FunctionID`Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen değerleri alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d4b5-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4b5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9d4b5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d4b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d4b5-105">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="9d4b5-106">'ndaki Değerleri alternatif değerleriyle eşlemek için çağrılacak [FunctionIDMapper](functionidmapper-function.md) uygulamasına yönelik bir işaretçi `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="9d4b5-106">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d4b5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d4b5-107">Remarks</span></span>  

 <span data-ttu-id="9d4b5-108">Değerler için alternatifler, `FunctionID` " [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) yöntemi tarafından belirtilen profil oluşturucunun işlev girdisine/çıkış kancalarına ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md)) geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="9d4b5-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="9d4b5-109">`FunctionIDMapper`Yalnızca bir kez ayarlanabilir ve bunu [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırması içinde ayarlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="9d4b5-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4b5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d4b5-110">Requirements</span></span>  

 <span data-ttu-id="9d4b5-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4b5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4b5-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d4b5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d4b5-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d4b5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d4b5-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d4b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4b5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d4b5-115">See also</span></span>

- [<span data-ttu-id="9d4b5-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d4b5-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
