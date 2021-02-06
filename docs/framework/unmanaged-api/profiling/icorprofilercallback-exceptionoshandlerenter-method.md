---
description: ': ICorProfilerCallback:: ExceptionOSHandlerEnter yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 88dfd062451c63265716e7cf4c04292aa15f91ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657625"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="fedd5-103">ICorProfilerCallback::ExceptionOSHandlerEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fedd5-103">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>

<span data-ttu-id="fedd5-104">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="fedd5-104">Not implemented.</span></span> <span data-ttu-id="fedd5-105">Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.</span><span class="sxs-lookup"><span data-stu-id="fedd5-105">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fedd5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fedd5-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fedd5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fedd5-107">Requirements</span></span>  

 <span data-ttu-id="fedd5-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fedd5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fedd5-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fedd5-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fedd5-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fedd5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fedd5-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fedd5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedd5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fedd5-112">See also</span></span>

- [<span data-ttu-id="fedd5-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fedd5-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
