---
title: "ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f0ae2be95b559074ca9dacde493a98008608b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="f6799-102">ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6799-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="f6799-103">Profil Oluşturucu uzaktan iletişim çağrısı, istemcide tamamlanıncaya kadar çalıştırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="f6799-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6799-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6799-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f6799-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6799-105">Remarks</span></span>  
 <span data-ttu-id="f6799-106">Uzaktan iletişim çağrısı zaman uyumlu değilse, bunu tamamlanıncaya kadar sunucuda çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="f6799-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="f6799-107">Uzaktan iletişim çağrısı zaman uyumsuz olduysa, çağrı işlendiğinde yanıt hala beklenen.</span><span class="sxs-lookup"><span data-stu-id="f6799-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="f6799-108">Bir yanıt bekleniyorsa yapılan bir çağrı olarak ortaya çıkar [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve ek bir arama `RemotingClientInvocationFinished` zaman uyumsuz bir çağrı gerekli ikincil işlenmesini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f6799-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="f6799-109">Geri aramalar aşağıdaki çiftleri her iş parçacığı üzerinde meydana gelir:</span><span class="sxs-lookup"><span data-stu-id="f6799-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="f6799-110">`RemotingClientInvocationStarted`ve [Icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="f6799-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="f6799-111">[Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve [Icorprofilercallback::remotingclientınvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="f6799-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="f6799-112">[Icorprofilercallback::remotingserverınvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) ve [Icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="f6799-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="f6799-113">Remoting geri çağırmaları ile ilgili aşağıdaki sorunları haberdar olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f6799-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="f6799-114">Bildirimler istemci tarafından çağrılan ve sunucu üzerinde yürütülen işlevler için düzgün şekilde alınmadı şekilde remoting işlevi yürütülmesi profil oluşturucu API, yansıtılmaz.</span><span class="sxs-lookup"><span data-stu-id="f6799-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="f6799-115">Gerçek çağrısını bir proxy nesnesi olur; Profil Oluşturucu için belirli işlevleri JIT derlenmiş ancak hiçbir zaman kullanılan görünür.</span><span class="sxs-lookup"><span data-stu-id="f6799-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="f6799-116">Profil Oluşturucu zaman uyumsuz remoting olayları için doğru bildirimleri almaz.</span><span class="sxs-lookup"><span data-stu-id="f6799-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6799-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6799-117">Requirements</span></span>  
 <span data-ttu-id="f6799-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6799-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6799-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f6799-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6799-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6799-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6799-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6799-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6799-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6799-122">See Also</span></span>  
 [<span data-ttu-id="f6799-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6799-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
