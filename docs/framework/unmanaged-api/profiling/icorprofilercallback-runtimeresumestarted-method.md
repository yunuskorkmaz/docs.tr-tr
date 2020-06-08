---
title: ICorProfilerCallback::RuntimeResumeStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
ms.openlocfilehash: 08e76e295e30ede48733ab35870ec965eb157f60
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499876"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="90e61-102">ICorProfilerCallback::RuntimeResumeStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90e61-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="90e61-103">Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürmeye devam etgeldiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="90e61-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90e61-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="90e61-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90e61-105">Requirements</span></span>  
 <span data-ttu-id="90e61-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90e61-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90e61-107">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="90e61-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90e61-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="90e61-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90e61-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90e61-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e61-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90e61-110">See also</span></span>

- [<span data-ttu-id="90e61-111">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90e61-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="90e61-112">RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90e61-112">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
