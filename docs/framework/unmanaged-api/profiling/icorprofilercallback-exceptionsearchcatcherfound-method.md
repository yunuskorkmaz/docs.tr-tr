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
ms.openlocfilehash: 12f16b9bc87ea65e2699ec902d717b08d3155b95
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756171"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="ded18-102">ICorProfilerCallback::ExceptionSearchCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ded18-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="ded18-103">Profil Oluşturucu, oluşturulan özel durum işleyicisi özel durum işleme arama aşaması bulunduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="ded18-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ded18-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ded18-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ded18-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ded18-106">[in] Özel durum işleyicisini içeren işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="ded18-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded18-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ded18-107">Requirements</span></span>  
 <span data-ttu-id="ded18-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ded18-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded18-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ded18-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ded18-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ded18-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ded18-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ded18-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded18-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ded18-112">See also</span></span>

- [<span data-ttu-id="ded18-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ded18-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
