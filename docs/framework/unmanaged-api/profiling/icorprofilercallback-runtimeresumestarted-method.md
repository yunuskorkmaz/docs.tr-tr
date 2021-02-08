---
description: ': ICorProfilerCallback:: RuntimeResumeStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 74e87906b4c429d795aa3074b25f4ac7a9edfa37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788845"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="f3cb0-103">ICorProfilerCallback::RuntimeResumeStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3cb0-103">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>

<span data-ttu-id="f3cb0-104">Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürmeye devam etgeldiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="f3cb0-104">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3cb0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3cb0-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f3cb0-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3cb0-106">Requirements</span></span>  

 <span data-ttu-id="f3cb0-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3cb0-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3cb0-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f3cb0-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3cb0-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f3cb0-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3cb0-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3cb0-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3cb0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3cb0-111">See also</span></span>

- [<span data-ttu-id="f3cb0-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3cb0-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f3cb0-113">RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3cb0-113">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
