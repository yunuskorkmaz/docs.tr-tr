---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
ms.openlocfilehash: 3f6320d6d962e40acf494acbb5c95adda62d1461
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445296"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="15d96-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15d96-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="15d96-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span><span class="sxs-lookup"><span data-stu-id="15d96-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15d96-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15d96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15d96-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="15d96-106">[in] The ID of the function that is being unwound.</span><span class="sxs-lookup"><span data-stu-id="15d96-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15d96-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15d96-107">Remarks</span></span>  
 <span data-ttu-id="15d96-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="15d96-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="15d96-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="15d96-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="15d96-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="15d96-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d96-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15d96-111">Requirements</span></span>  
 <span data-ttu-id="15d96-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d96-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d96-113">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15d96-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15d96-114">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15d96-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15d96-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d96-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d96-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15d96-116">See also</span></span>

- [<span data-ttu-id="15d96-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15d96-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="15d96-118">ExceptionUnwindFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15d96-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
