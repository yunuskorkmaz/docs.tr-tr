---
title: ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 01404d23707be90b6b15cf741632400d49f164de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445141"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="bf499-102">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf499-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="bf499-103">Notifies the profiler that an assembly has been unloaded.</span><span class="sxs-lookup"><span data-stu-id="bf499-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf499-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf499-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf499-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf499-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="bf499-106">[in] Identifies the assembly that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="bf499-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="bf499-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span><span class="sxs-lookup"><span data-stu-id="bf499-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf499-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf499-108">Remarks</span></span>  
 <span data-ttu-id="bf499-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span><span class="sxs-lookup"><span data-stu-id="bf499-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="bf499-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="bf499-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="bf499-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="bf499-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="bf499-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span><span class="sxs-lookup"><span data-stu-id="bf499-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf499-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf499-113">Requirements</span></span>  
 <span data-ttu-id="bf499-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf499-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf499-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf499-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf499-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf499-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf499-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf499-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf499-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf499-118">See also</span></span>

- [<span data-ttu-id="bf499-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf499-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
