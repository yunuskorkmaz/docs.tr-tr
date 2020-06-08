---
title: ICorProfilerCallback::RemotingClientInvocationStarted Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 8a042e71690b5ae77c1e4cda7be394a163ab2774
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503269"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="98bae-102">ICorProfilerCallback::RemotingClientInvocationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98bae-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="98bae-103">Profil oluşturucuyu, uzaktan iletişim çağrısının başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="98bae-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98bae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98bae-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="98bae-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98bae-105">Remarks</span></span>  
 <span data-ttu-id="98bae-106">Bu olay, zaman uyumlu ve zaman uyumsuz çağrılar için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="98bae-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="98bae-107">Aşağıdaki geri arama çiftlerinin her biri aynı iş parçacığında gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="98bae-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="98bae-108">`RemotingClientInvocationStarted`ve [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="98bae-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="98bae-109">[ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) ve [ICorProfilerCallback:: RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="98bae-109">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="98bae-110">[ICorProfilerCallback:: Remotingserverınvocationdöndürüldü](icorprofilercallback-remotingserverinvocationreturned-method.md) ve [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="98bae-110">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="98bae-111">Uzaktan iletişim geri çağırmalar ile ilgili aşağıdaki sorunları bilmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="98bae-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="98bae-112">Bir uzaktan iletişim işlevinin yürütülmesi profil oluşturucu API 'SI tarafından yansıtılmadığından, istemciden çağrılan ve sunucuda yürütülen işlevlere yönelik bildirimler düzgün bir şekilde alınmaz.</span><span class="sxs-lookup"><span data-stu-id="98bae-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="98bae-113">Gerçek çağrı bir proxy nesnesi aracılığıyla gerçekleşir; Profil Oluşturucu için, belirli işlevlerin JıT olarak derlendiğini ancak hiç kullanılmayacağını görünür.</span><span class="sxs-lookup"><span data-stu-id="98bae-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="98bae-114">Profil Oluşturucu, zaman uyumsuz uzaktan iletişim olayları için doğru bildirimler almaz.</span><span class="sxs-lookup"><span data-stu-id="98bae-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98bae-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98bae-115">Requirements</span></span>  
 <span data-ttu-id="98bae-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98bae-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98bae-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="98bae-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98bae-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98bae-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98bae-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98bae-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98bae-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98bae-120">See also</span></span>

- [<span data-ttu-id="98bae-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98bae-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
