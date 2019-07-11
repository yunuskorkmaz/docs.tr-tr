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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 710a33583e45b27cec66278f4e20152acfae97dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782876"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="ebda1-102">ICorProfilerCallback::RemotingServerInvocationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebda1-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="ebda1-103">Profil Oluşturucu işlemi uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağıran olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="ebda1-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebda1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebda1-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ebda1-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebda1-105">Requirements</span></span>  
 <span data-ttu-id="ebda1-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebda1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebda1-107">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ebda1-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ebda1-108">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebda1-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebda1-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebda1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebda1-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebda1-110">See also</span></span>

- [<span data-ttu-id="ebda1-111">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebda1-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
