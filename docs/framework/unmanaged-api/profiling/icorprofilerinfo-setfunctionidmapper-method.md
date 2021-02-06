---
description: ': ICorProfilerInfo:: SetFunctionIDMapper yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c03c225db3b4126c3ac46ef6e5d36a5f72e529f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647225"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="7ca90-103">ICorProfilerInfo::SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ca90-103">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>

<span data-ttu-id="7ca90-104">`FunctionID`Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen değerleri alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ca90-104">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca90-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ca90-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ca90-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ca90-106">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="7ca90-107">'ndaki Değerleri alternatif değerleriyle eşlemek için çağrılacak [FunctionIDMapper](functionidmapper-function.md) uygulamasına yönelik bir işaretçi `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="7ca90-107">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ca90-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ca90-108">Remarks</span></span>  

 <span data-ttu-id="7ca90-109">Değerler için alternatifler, `FunctionID` " [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) yöntemi tarafından belirtilen profil oluşturucunun işlev girdisine/çıkış kancalarına ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md)) geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="7ca90-109">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="7ca90-110">`FunctionIDMapper`Yalnızca bir kez ayarlanabilir ve bunu [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırması içinde ayarlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="7ca90-110">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca90-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ca90-111">Requirements</span></span>  

 <span data-ttu-id="7ca90-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ca90-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca90-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7ca90-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ca90-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ca90-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ca90-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ca90-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca90-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ca90-116">See also</span></span>

- [<span data-ttu-id="7ca90-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ca90-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
