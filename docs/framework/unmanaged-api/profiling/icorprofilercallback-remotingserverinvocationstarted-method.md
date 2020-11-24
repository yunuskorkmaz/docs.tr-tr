---
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
ms.openlocfilehash: 630efefde2a90eca0b40643ea8d7ffe08efdc763
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676835"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="cc9dc-102">ICorProfilerCallback::RemotingServerInvocationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc9dc-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>

<span data-ttu-id="cc9dc-103">Profil oluşturucuyu, işlemin uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağırdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="cc9dc-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc9dc-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cc9dc-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="cc9dc-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc9dc-105">Requirements</span></span>  

 <span data-ttu-id="cc9dc-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc9dc-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc9dc-107">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cc9dc-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc9dc-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc9dc-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc9dc-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc9dc-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9dc-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc9dc-110">See also</span></span>

- [<span data-ttu-id="cc9dc-111">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc9dc-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
