---
description: ': ICorProfilerCallback:: ExceptionSearchCatcherFound yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ExceptionSearchCatcherFound Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: b222e629cbfce2fde27c2d266b3a343466a1419c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706324"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="dd77f-103">ICorProfilerCallback::ExceptionSearchCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd77f-103">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>

<span data-ttu-id="dd77f-104">Profil oluşturucuya özel durum işlemenin arama aşamasının oluşturulan özel durum için bir işleyici bulunduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="dd77f-104">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd77f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd77f-105">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd77f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd77f-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="dd77f-107">\[' de] özel durum işleyicisini içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd77f-107">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="dd77f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd77f-108">Requirements</span></span>  

 <span data-ttu-id="dd77f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd77f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd77f-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dd77f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd77f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dd77f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd77f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd77f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd77f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd77f-113">See also</span></span>

- [<span data-ttu-id="dd77f-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd77f-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
