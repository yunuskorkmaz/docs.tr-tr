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
ms.openlocfilehash: d9167b35556fafb33e61e1dc050488aec2b7fa01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776015"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="36be4-102">ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36be4-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="36be4-103">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="36be4-103">Not implemented.</span></span> <span data-ttu-id="36be4-104">Yönetilmeyen özel durum bilgisi gerektiren bir profil oluşturucu, diğer araçlarla bu bilgileri edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36be4-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36be4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36be4-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="36be4-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36be4-106">Requirements</span></span>  
 <span data-ttu-id="36be4-107">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36be4-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36be4-108">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36be4-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36be4-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36be4-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36be4-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36be4-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36be4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36be4-111">See also</span></span>

- [<span data-ttu-id="36be4-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36be4-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
