---
title: "ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c6ba73ef9551c599c07c4021ff8fff85d53c4a84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="56bad-102">ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56bad-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="56bad-103">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="56bad-103">Not implemented.</span></span> <span data-ttu-id="56bad-104">Yönetilmeyen özel durum bilgileri gerektiren bir profil oluşturucu arasında başka yollarla bu bilgileri edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56bad-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56bad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56bad-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="56bad-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56bad-106">Requirements</span></span>  
 <span data-ttu-id="56bad-107">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56bad-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56bad-108">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56bad-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56bad-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56bad-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56bad-110">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56bad-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56bad-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56bad-111">See Also</span></span>  
 [<span data-ttu-id="56bad-112">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="56bad-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
