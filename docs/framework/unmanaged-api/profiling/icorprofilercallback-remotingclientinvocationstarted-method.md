---
description: ': ICorProfilerCallback:: RemotingClientInvocationStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3727383c3a23fa9e4327970e84c6ebde4ab14db0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788975"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="f3fb8-103">ICorProfilerCallback::RemotingClientInvocationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3fb8-103">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>

<span data-ttu-id="f3fb8-104">Profil oluşturucuyu, uzaktan iletişim çağrısının başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="f3fb8-104">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fb8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3fb8-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f3fb8-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3fb8-106">Remarks</span></span>  

 <span data-ttu-id="f3fb8-107">Bu olay, zaman uyumlu ve zaman uyumsuz çağrılar için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f3fb8-107">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="f3fb8-108">Aşağıdaki geri arama çiftlerinin her biri aynı iş parçacığında gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="f3fb8-108">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="f3fb8-109">`RemotingClientInvocationStarted` ve [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="f3fb8-109">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="f3fb8-110">[ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) ve [ICorProfilerCallback:: RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="f3fb8-110">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="f3fb8-111">[ICorProfilerCallback:: Remotingserverınvocationdöndürüldü](icorprofilercallback-remotingserverinvocationreturned-method.md) ve [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="f3fb8-111">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="f3fb8-112">Uzaktan iletişim geri çağırmalar ile ilgili aşağıdaki sorunları bilmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="f3fb8-112">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="f3fb8-113">Bir uzaktan iletişim işlevinin yürütülmesi profil oluşturucu API 'SI tarafından yansıtılmadığından, istemciden çağrılan ve sunucuda yürütülen işlevlere yönelik bildirimler düzgün bir şekilde alınmaz.</span><span class="sxs-lookup"><span data-stu-id="f3fb8-113">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="f3fb8-114">Gerçek çağrı bir proxy nesnesi aracılığıyla gerçekleşir; Profil Oluşturucu için, belirli işlevlerin JıT olarak derlendiğini ancak hiç kullanılmayacağını görünür.</span><span class="sxs-lookup"><span data-stu-id="f3fb8-114">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="f3fb8-115">Profil Oluşturucu, zaman uyumsuz uzaktan iletişim olayları için doğru bildirimler almaz.</span><span class="sxs-lookup"><span data-stu-id="f3fb8-115">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fb8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3fb8-116">Requirements</span></span>  

 <span data-ttu-id="f3fb8-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3fb8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fb8-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f3fb8-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3fb8-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f3fb8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3fb8-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fb8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fb8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3fb8-121">See also</span></span>

- [<span data-ttu-id="f3fb8-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3fb8-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
