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
ms.openlocfilehash: 273c3cefa2e67a7d8c429982b4da4126168b2830
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699969"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="f137e-102">ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f137e-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>

<span data-ttu-id="f137e-103">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="f137e-103">Not implemented.</span></span> <span data-ttu-id="f137e-104">Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.</span><span class="sxs-lookup"><span data-stu-id="f137e-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f137e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f137e-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f137e-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f137e-106">Requirements</span></span>  

 <span data-ttu-id="f137e-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f137e-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f137e-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f137e-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f137e-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f137e-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f137e-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f137e-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f137e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f137e-111">See also</span></span>

- [<span data-ttu-id="f137e-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f137e-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
