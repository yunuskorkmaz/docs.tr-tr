---
title: "ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchFilterEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 129bc39fc9edd8f3101e7d03272bcab35c746d73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="29671-102">ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29671-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="29671-103">Profil Oluşturucu kullanıcı tanımlı özel durum filtresi yürütülürken özel durum işleme arama aşaması başladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="29671-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29671-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29671-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29671-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29671-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="29671-106">[in] Filtre içeriyor işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="29671-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29671-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29671-107">Requirements</span></span>  
 <span data-ttu-id="29671-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29671-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29671-109">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29671-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29671-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29671-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29671-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29671-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29671-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29671-112">See Also</span></span>  
 [<span data-ttu-id="29671-113">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="29671-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="29671-114">ExceptionSearchFilterLeave yöntemi</span><span class="sxs-lookup"><span data-stu-id="29671-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
