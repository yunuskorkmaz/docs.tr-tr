---
title: "ICorProfilerCallback2::HandleCreated Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d920f2e33a43e36c7bf27b4e1a88d6bc4a23600
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="8faa8-102">ICorProfilerCallback2::HandleCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8faa8-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="8faa8-103">Kod profil oluşturucu bir atık toplama tanıtıcı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="8faa8-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8faa8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8faa8-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8faa8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8faa8-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="8faa8-106">[in] Çöp toplama için tanıtıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="8faa8-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="8faa8-107">[in] Çöp toplama tanıtıcı oluşturulduğu nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="8faa8-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8faa8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8faa8-108">Requirements</span></span>  
 <span data-ttu-id="8faa8-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8faa8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8faa8-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8faa8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8faa8-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8faa8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8faa8-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8faa8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8faa8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8faa8-113">See Also</span></span>  
 [<span data-ttu-id="8faa8-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8faa8-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8faa8-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8faa8-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
