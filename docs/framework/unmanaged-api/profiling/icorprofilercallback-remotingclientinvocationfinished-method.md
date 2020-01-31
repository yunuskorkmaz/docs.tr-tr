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
ms.openlocfilehash: 90ddb30c3d27d5f431c355abd3a6f792564e616d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866057"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="7bd2d-102">ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bd2d-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="7bd2d-103">Bir uzaktan iletişim çağrısının istemci üzerinde tamamlanmasının çalıştırıldığı profil oluşturucuyu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd2d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bd2d-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7bd2d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bd2d-105">Remarks</span></span>  
 <span data-ttu-id="7bd2d-106">Uzaktan iletişim çağrısı zaman uyumlu ise, sunucuda tamamlanmayı da çalıştırmıştır.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="7bd2d-107">Uzaktan iletişim çağrısı zaman uyumsuz ise, çağrı işlendiği zaman yanıt beklenmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="7bd2d-108">Bir yanıt bekleniyorsa, [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) çağrısı ve bir zaman uyumsuz çağrının gerekli ikincil işlemesini göstermek için `RemotingClientInvocationFinished` ek bir çağrı olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="7bd2d-109">Aşağıdaki geri arama çiftlerinin her biri aynı iş parçacığında gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="7bd2d-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="7bd2d-110">`RemotingClientInvocationStarted` ve [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="7bd2d-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="7bd2d-111">[ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) ve [ICorProfilerCallback:: RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="7bd2d-111">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="7bd2d-112">[ICorProfilerCallback:: Remotingserverınvocationdöndürüldü](icorprofilercallback-remotingserverinvocationreturned-method.md) ve [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="7bd2d-112">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="7bd2d-113">Uzaktan iletişim geri çağırmalar ile ilgili aşağıdaki sorunları bilmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="7bd2d-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="7bd2d-114">Bir uzaktan iletişim işlevinin yürütülmesi profil oluşturucu API 'SI tarafından yansıtılmadığından, istemciden çağrılan ve sunucuda yürütülen işlevlere yönelik bildirimler düzgün bir şekilde alınmaz.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="7bd2d-115">Gerçek çağrı bir proxy nesnesi aracılığıyla gerçekleşir; Profil Oluşturucu için, belirli işlevlerin JıT olarak derlendiğini ancak hiç kullanılmayacağını görünür.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="7bd2d-116">Profil Oluşturucu, zaman uyumsuz uzaktan iletişim olayları için doğru bildirimler almaz.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bd2d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bd2d-117">Requirements</span></span>  
 <span data-ttu-id="7bd2d-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bd2d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bd2d-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7bd2d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bd2d-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7bd2d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bd2d-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bd2d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd2d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd2d-122">See also</span></span>

- [<span data-ttu-id="7bd2d-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bd2d-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
