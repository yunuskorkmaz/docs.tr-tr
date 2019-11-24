---
title: ICorProfilerCallback::ModuleUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: 40cb666c47c690dc930ec2cb7f6c89662464780e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445914"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="26475-102">ICorProfilerCallback::ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26475-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="26475-103">Notifies the profiler that a module has finished unloading.</span><span class="sxs-lookup"><span data-stu-id="26475-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26475-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26475-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26475-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26475-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="26475-106">[in] The ID of the module that was unloaded.</span><span class="sxs-lookup"><span data-stu-id="26475-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="26475-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span><span class="sxs-lookup"><span data-stu-id="26475-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26475-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26475-108">Remarks</span></span>  
 <span data-ttu-id="26475-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span><span class="sxs-lookup"><span data-stu-id="26475-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="26475-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="26475-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="26475-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="26475-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="26475-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span><span class="sxs-lookup"><span data-stu-id="26475-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26475-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26475-113">Requirements</span></span>  
 <span data-ttu-id="26475-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26475-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26475-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26475-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26475-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26475-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26475-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26475-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26475-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26475-118">See also</span></span>

- [<span data-ttu-id="26475-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26475-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
