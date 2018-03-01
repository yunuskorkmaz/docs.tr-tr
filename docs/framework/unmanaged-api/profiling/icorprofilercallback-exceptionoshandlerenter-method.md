---
title: "ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi"
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
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c26260a2f70537deefb5600c0b721e0c0faf0399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="b2f24-102">ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2f24-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="b2f24-103">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="b2f24-103">Not implemented.</span></span> <span data-ttu-id="b2f24-104">Yönetilmeyen özel durum bilgileri gerektiren bir profil oluşturucu arasında başka yollarla bu bilgileri edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2f24-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f24-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2f24-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b2f24-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2f24-106">Requirements</span></span>  
 <span data-ttu-id="b2f24-107">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2f24-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2f24-108">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2f24-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2f24-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2f24-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2f24-110">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2f24-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f24-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2f24-111">See Also</span></span>  
 [<span data-ttu-id="b2f24-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2f24-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
