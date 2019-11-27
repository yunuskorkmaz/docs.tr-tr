---
title: ICorProfilerCallback::AssemblyLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: 34744132442440ef160841db5a50bf75355f2410
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445165"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="adae4-102">ICorProfilerCallback::AssemblyLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="adae4-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="adae4-103">Profiler 'ın bir derlemenin yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="adae4-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adae4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adae4-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adae4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="adae4-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="adae4-106">'ndaki Yüklenmekte olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="adae4-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adae4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adae4-107">Remarks</span></span>  
 <span data-ttu-id="adae4-108">`assemblyId` değeri, [ICorProfilerCallback:: AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="adae4-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adae4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="adae4-109">Requirements</span></span>  
 <span data-ttu-id="adae4-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adae4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adae4-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="adae4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="adae4-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="adae4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adae4-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adae4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adae4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adae4-114">See also</span></span>

- [<span data-ttu-id="adae4-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adae4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
