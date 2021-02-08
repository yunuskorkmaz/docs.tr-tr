---
description: ': ICorProfilerCallback:: RemotingServerInvocationStarted yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RemotingServerInvocationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
ms.openlocfilehash: 8a27e3e545b9ff2812561f5faa7ebfe70d41f015
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788910"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="dde3a-103">ICorProfilerCallback::RemotingServerInvocationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dde3a-103">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>

<span data-ttu-id="dde3a-104">Profil oluşturucuyu, işlemin uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağırdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dde3a-104">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde3a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dde3a-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="dde3a-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dde3a-106">Requirements</span></span>  

 <span data-ttu-id="dde3a-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde3a-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde3a-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dde3a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dde3a-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dde3a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dde3a-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dde3a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde3a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dde3a-111">See also</span></span>

- [<span data-ttu-id="dde3a-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dde3a-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
