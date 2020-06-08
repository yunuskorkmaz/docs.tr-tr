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
ms.openlocfilehash: df172edb97a82ae3bf2d46c8be6ea05d5445a09a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500435"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="60a7e-102">ICorProfilerCallback::AssemblyLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60a7e-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="60a7e-103">Profiler 'ın bir derlemenin yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="60a7e-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a7e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="60a7e-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60a7e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60a7e-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="60a7e-106">\[' de] yüklenmekte olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60a7e-106">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="60a7e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60a7e-107">Remarks</span></span>  
 <span data-ttu-id="60a7e-108">Değeri, `assemblyId` [ICorProfilerCallback:: AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="60a7e-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a7e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60a7e-109">Requirements</span></span>  
 <span data-ttu-id="60a7e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a7e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a7e-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="60a7e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60a7e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="60a7e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60a7e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a7e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a7e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60a7e-114">See also</span></span>

- [<span data-ttu-id="60a7e-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60a7e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
