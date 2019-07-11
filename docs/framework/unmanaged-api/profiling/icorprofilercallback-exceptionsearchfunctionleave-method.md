---
title: ICorProfilerCallback::ExceptionSearchFunctionLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad694f1a041346bc360e623829d2d38245773aaf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756077"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="ada31-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ada31-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="ada31-103">Profil Oluşturucu, özel durum işleme arama aşaması bir işlev arama işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ada31-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ada31-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ada31-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ada31-105">Requirements</span></span>  
 <span data-ttu-id="ada31-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada31-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada31-107">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ada31-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ada31-108">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ada31-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ada31-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada31-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada31-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ada31-110">See also</span></span>

- [<span data-ttu-id="ada31-111">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ada31-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ada31-112">ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ada31-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
