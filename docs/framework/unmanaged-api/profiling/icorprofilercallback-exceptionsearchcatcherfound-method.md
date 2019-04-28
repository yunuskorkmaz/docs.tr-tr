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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e41378b314b91f42fca9d1039d3011b5eaafe502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598359"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="5416f-102">ICorProfilerCallback::ExceptionSearchCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5416f-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="5416f-103">Profil Oluşturucu, oluşturulan özel durum işleyicisi özel durum işleme arama aşaması bulunduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5416f-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5416f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5416f-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5416f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5416f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5416f-106">[in] Özel durum işleyicisini içeren işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="5416f-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5416f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5416f-107">Requirements</span></span>  
 <span data-ttu-id="5416f-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5416f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5416f-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5416f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5416f-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5416f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5416f-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5416f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5416f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5416f-112">See also</span></span>

- [<span data-ttu-id="5416f-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5416f-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
