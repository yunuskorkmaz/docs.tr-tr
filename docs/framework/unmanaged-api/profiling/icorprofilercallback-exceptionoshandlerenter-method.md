---
title: ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2dc7c22ee075f347604864d8bee1a4e871da616
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451772"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="888ed-102">ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="888ed-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="888ed-103">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="888ed-103">Not implemented.</span></span> <span data-ttu-id="888ed-104">Yönetilmeyen özel durum bilgileri gerektiren bir profil oluşturucu arasında başka yollarla bu bilgileri edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="888ed-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="888ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="888ed-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="888ed-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="888ed-106">Requirements</span></span>  
 <span data-ttu-id="888ed-107">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="888ed-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="888ed-108">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="888ed-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="888ed-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="888ed-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="888ed-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="888ed-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888ed-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="888ed-111">See Also</span></span>  
 [<span data-ttu-id="888ed-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="888ed-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
