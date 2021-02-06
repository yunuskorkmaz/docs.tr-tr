---
description: ': ICorProfilerCallback:: AssemblyLoadStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f771008b9aed9322f0c5fd279fa9dfb3086755e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648025"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="08626-103">ICorProfilerCallback::AssemblyLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08626-103">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>

<span data-ttu-id="08626-104">Profiler 'ın bir derlemenin yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="08626-104">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08626-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08626-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08626-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08626-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="08626-107">\[' de] yüklenmekte olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08626-107">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="08626-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08626-108">Remarks</span></span>  

 <span data-ttu-id="08626-109">Değeri, `assemblyId` [ICorProfilerCallback:: AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="08626-109">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08626-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08626-110">Requirements</span></span>  

 <span data-ttu-id="08626-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08626-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08626-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="08626-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08626-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08626-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08626-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08626-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08626-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08626-115">See also</span></span>

- [<span data-ttu-id="08626-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08626-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
