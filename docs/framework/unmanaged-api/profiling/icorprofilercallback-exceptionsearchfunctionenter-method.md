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
ms.openlocfilehash: 48af2d4738d09a3b3701e0b4d6bf18209bffa6d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450778"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="e2722-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2722-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="e2722-103">Profil Oluşturucu, arama için geçerli özel durum işleyici bulmak için bir işlev özel durum işleme arama aşaması başladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="e2722-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2722-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2722-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2722-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2722-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e2722-106">[in] Girilen işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="e2722-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2722-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2722-107">Requirements</span></span>  
 <span data-ttu-id="e2722-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2722-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2722-109">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2722-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2722-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2722-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2722-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2722-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2722-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2722-112">See Also</span></span>  
 [<span data-ttu-id="e2722-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2722-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e2722-114">ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2722-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
