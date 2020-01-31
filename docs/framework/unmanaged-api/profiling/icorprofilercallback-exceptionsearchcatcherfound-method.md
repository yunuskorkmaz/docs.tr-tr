---
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
ms.openlocfilehash: 8f5997dddf78dd75d482bc45d2ee730b20d9ab16
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866484"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="bec13-102">ICorProfilerCallback::ExceptionSearchCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bec13-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="bec13-103">Profil oluşturucuya özel durum işlemenin arama aşamasının oluşturulan özel durum için bir işleyici bulunduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="bec13-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bec13-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bec13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bec13-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="bec13-106">\[in] özel durum işleyicisini içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bec13-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="bec13-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bec13-107">Requirements</span></span>  
 <span data-ttu-id="bec13-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bec13-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bec13-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bec13-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bec13-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bec13-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bec13-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec13-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec13-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bec13-112">See also</span></span>

- [<span data-ttu-id="bec13-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bec13-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
