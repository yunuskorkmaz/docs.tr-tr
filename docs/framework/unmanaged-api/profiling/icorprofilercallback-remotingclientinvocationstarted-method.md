---
title: "ICorProfilerCallback::RemotingClientInvocationStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 071e2892202271cac5e0acb226e9bef0e626b134
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="daf46-102">ICorProfilerCallback::RemotingClientInvocationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="daf46-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="daf46-103">Profil Oluşturucu uzaktan iletişim çağrısı başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="daf46-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daf46-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="daf46-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="daf46-105">Remarks</span></span>  
 <span data-ttu-id="daf46-106">Bu olay, zaman uyumlu ve zaman uyumsuz çağrıları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="daf46-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="daf46-107">Geri aramalar aşağıdaki çiftleri her iş parçacığı üzerinde meydana gelir:</span><span class="sxs-lookup"><span data-stu-id="daf46-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="daf46-108">`RemotingClientInvocationStarted`ve [Icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="daf46-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="daf46-109">[Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve [Icorprofilercallback::remotingclientınvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="daf46-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="daf46-110">[Icorprofilercallback::remotingserverınvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) ve [Icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="daf46-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="daf46-111">Remoting geri çağırmaları ile ilgili aşağıdaki sorunları haberdar olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="daf46-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="daf46-112">Bildirimler istemci tarafından çağrılan ve sunucu üzerinde yürütülen işlevler için düzgün şekilde alınmadı şekilde remoting işlevi yürütülmesi profil oluşturucu API, yansıtılmaz.</span><span class="sxs-lookup"><span data-stu-id="daf46-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="daf46-113">Gerçek çağrısını bir proxy nesnesi olur; Profil Oluşturucu için belirli işlevleri JIT derlenmiş ancak hiçbir zaman kullanılan görünür.</span><span class="sxs-lookup"><span data-stu-id="daf46-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="daf46-114">Profil Oluşturucu zaman uyumsuz remoting olayları için doğru bildirimleri almaz.</span><span class="sxs-lookup"><span data-stu-id="daf46-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daf46-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="daf46-115">Requirements</span></span>  
 <span data-ttu-id="daf46-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daf46-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daf46-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="daf46-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="daf46-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daf46-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daf46-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daf46-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf46-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="daf46-120">See Also</span></span>  
 [<span data-ttu-id="daf46-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="daf46-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
