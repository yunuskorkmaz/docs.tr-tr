---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e631b0a90498ea1299d9448507014081bd2d3018
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756047"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="673fa-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="673fa-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="673fa-103">Profil Oluşturucu, özel durum işleme arama aşaması bir işlev için geçerli özel durum işleyici bulmak için arama başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="673fa-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="673fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="673fa-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="673fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="673fa-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="673fa-106">[in] Girilen işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="673fa-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="673fa-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="673fa-107">Requirements</span></span>  
 <span data-ttu-id="673fa-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="673fa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="673fa-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="673fa-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="673fa-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="673fa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="673fa-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="673fa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673fa-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="673fa-112">See also</span></span>

- [<span data-ttu-id="673fa-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="673fa-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="673fa-114">ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="673fa-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
