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
ms.openlocfilehash: c2c9ed848984d36ddf10d32d120deda76a4d47cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500292"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="4c9a8-102">ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c9a8-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="4c9a8-103">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-103">Not implemented.</span></span> <span data-ttu-id="4c9a8-104">Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c9a8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c9a8-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4c9a8-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c9a8-106">Requirements</span></span>  
 <span data-ttu-id="4c9a8-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c9a8-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c9a8-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4c9a8-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c9a8-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c9a8-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c9a8-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c9a8-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9a8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c9a8-111">See also</span></span>

- [<span data-ttu-id="4c9a8-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c9a8-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
