---
title: "ICorProfilerCallback::ExceptionSearchFunctionLeave Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 063b8e666b122103c6776b86aa86d1215e200016
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="1c4e0-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c4e0-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="1c4e0-103">Profil Oluşturucu, özel durum işleme arama aşaması işlevi aramayı bitirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c4e0-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c4e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c4e0-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="1c4e0-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c4e0-105">Requirements</span></span>  
 <span data-ttu-id="1c4e0-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c4e0-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c4e0-107">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c4e0-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c4e0-108">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c4e0-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c4e0-109">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c4e0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4e0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c4e0-110">See Also</span></span>  
 [<span data-ttu-id="1c4e0-111">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c4e0-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="1c4e0-112">ExceptionSearchFunctionEnter yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c4e0-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
