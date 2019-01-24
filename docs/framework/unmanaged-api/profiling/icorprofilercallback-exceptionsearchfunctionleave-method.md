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
ms.openlocfilehash: 6d20aa04b292fd29b60d68b844ef410258d90d31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546588"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="eaad3-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaad3-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="eaad3-103">Profil Oluşturucu, özel durum işleme arama aşaması bir işlev arama işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="eaad3-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaad3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaad3-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="eaad3-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaad3-105">Requirements</span></span>  
 <span data-ttu-id="eaad3-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaad3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaad3-107">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eaad3-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eaad3-108">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaad3-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaad3-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaad3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaad3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaad3-110">See also</span></span>
- [<span data-ttu-id="eaad3-111">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaad3-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="eaad3-112">ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaad3-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
