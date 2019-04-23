---
title: ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2722497db5622dee4adcfd9381837477b89a8f63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206583"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="77034-102">ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77034-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="77034-103">Profil Oluşturucu bir çağrının sürebileceği istemcide tamamlanmak üzere çalıştırılmasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="77034-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77034-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77034-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="77034-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77034-105">Remarks</span></span>  
 <span data-ttu-id="77034-106">Uzaktan iletişim çağrısı, zaman uyumlu ise, bunu tamamlanana kadar sunucuda çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="77034-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="77034-107">Zaman uyumsuz bir çağrının sürebileceği olduysa, çağrı işlendiğinde yanıt hala beklenebilir.</span><span class="sxs-lookup"><span data-stu-id="77034-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="77034-108">Bir yanıt bekleniyorsa, bir çağrı olarak ortaya çıkar [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve ek bir arama `RemotingClientInvocationFinished` zaman uyumsuz bir çağrı gerekli ikincil işlenmesini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="77034-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="77034-109">Her biri aşağıdaki geri çağırmalar çiftleri aynı iş parçacığında ortaya çıkar:</span><span class="sxs-lookup"><span data-stu-id="77034-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="77034-110">`RemotingClientInvocationStarted` ve [Icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="77034-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="77034-111">[Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve [Icorprofilercallback::remotingclientınvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="77034-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="77034-112">[Icorprofilercallback::remotingserverınvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) ve [Icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="77034-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="77034-113">Uzaktan iletişimini geri çağırmaları ile ilgili aşağıdaki sorunları farkında olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="77034-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="77034-114">İstemciden çağrılan ve sunucu üzerinde yürütülen işlevler için bildirimler düzgün alınmadı şekilde profil oluşturucu API, uzak bir işlevin yürütülmesini yansıtılmaz.</span><span class="sxs-lookup"><span data-stu-id="77034-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="77034-115">Gerçek çağrısını bir proxy nesnesi olur; Profil Oluşturucu için bazı işlevlerini JIT olarak derlenmiş ancak hiçbir zaman kullanılan görünür.</span><span class="sxs-lookup"><span data-stu-id="77034-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="77034-116">Profil Oluşturucu, zaman uyumsuz uzaktan iletişim olayları için doğru bildirimleri almaz.</span><span class="sxs-lookup"><span data-stu-id="77034-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77034-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77034-117">Requirements</span></span>  
 <span data-ttu-id="77034-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77034-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77034-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77034-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77034-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77034-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77034-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77034-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77034-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77034-122">See also</span></span>

- [<span data-ttu-id="77034-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77034-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
