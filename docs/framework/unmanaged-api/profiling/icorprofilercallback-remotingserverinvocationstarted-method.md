---
title: "ICorProfilerCallback::RemotingServerInvocationStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerInvocationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c4e1fd36c7c6a1a3c4df8dfa233206de51676af1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="9184a-102">ICorProfilerCallback::RemotingServerInvocationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9184a-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="9184a-103">Profil Oluşturucu işlemi uzak yöntem çağırma isteğine yanıt olarak bir yönteminin çağrılması gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="9184a-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9184a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9184a-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="9184a-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9184a-105">Requirements</span></span>  
 <span data-ttu-id="9184a-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9184a-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9184a-107">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9184a-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9184a-108">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9184a-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9184a-109">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9184a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9184a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9184a-110">See Also</span></span>  
 [<span data-ttu-id="9184a-111">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="9184a-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
