---
title: ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9dd6345cb8b930136f1219144540fde96429a71b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478615"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="83148-102">ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83148-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="83148-103">Profil Oluşturucu, bir kullanıcı tanımlı özel durum filtresi yürütülürken özel durum işleme arama aşaması başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="83148-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83148-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83148-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83148-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83148-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="83148-106">[in] Filtre içeren işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="83148-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83148-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83148-107">Requirements</span></span>  
 <span data-ttu-id="83148-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83148-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83148-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83148-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83148-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83148-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83148-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83148-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83148-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83148-112">See also</span></span>
- [<span data-ttu-id="83148-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83148-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="83148-114">ExceptionSearchFilterLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83148-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
