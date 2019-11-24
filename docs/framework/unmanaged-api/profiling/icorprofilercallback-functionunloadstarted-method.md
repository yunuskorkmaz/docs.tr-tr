---
title: ICorProfilerCallback::FunctionUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: f57a3ed70267de65daed85305ad7d623b4ca0337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448024"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="f40ae-102">ICorProfilerCallback::FunctionUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f40ae-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="f40ae-103">Notifies the profiler that the runtime has started to unload a function.</span><span class="sxs-lookup"><span data-stu-id="f40ae-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f40ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f40ae-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="f40ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f40ae-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f40ae-106">[in] The ID of the function that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="f40ae-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f40ae-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f40ae-107">Remarks</span></span>  
 <span data-ttu-id="f40ae-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span><span class="sxs-lookup"><span data-stu-id="f40ae-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40ae-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f40ae-109">Requirements</span></span>  
 <span data-ttu-id="f40ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f40ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f40ae-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f40ae-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f40ae-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f40ae-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f40ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f40ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40ae-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f40ae-114">See also</span></span>

- [<span data-ttu-id="f40ae-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f40ae-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
