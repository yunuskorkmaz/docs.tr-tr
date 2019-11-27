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
ms.openlocfilehash: c9a750b941b29047206c98410d4b4673d1101a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445836"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="7745b-102">ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7745b-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="7745b-103">Bir uzaktan iletişim çağrısının istemci üzerinde tamamlanmasının çalıştırıldığı profil oluşturucuyu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7745b-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7745b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7745b-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7745b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7745b-105">Remarks</span></span>  
 <span data-ttu-id="7745b-106">Uzaktan iletişim çağrısı zaman uyumlu ise, sunucuda tamamlanmayı da çalıştırmıştır.</span><span class="sxs-lookup"><span data-stu-id="7745b-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="7745b-107">Uzaktan iletişim çağrısı zaman uyumsuz ise, çağrı işlendiği zaman yanıt beklenmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="7745b-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="7745b-108">Bir yanıt bekleniyorsa, [ICorProfilerCallback:: RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) çağrısı ve bir zaman uyumsuz çağrının gerekli ikincil işlemesini göstermek için `RemotingClientInvocationFinished` ek bir çağrı olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7745b-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="7745b-109">Aşağıdaki geri arama çiftlerinin her biri aynı iş parçacığında gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="7745b-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="7745b-110">`RemotingClientInvocationStarted` ve [ICorProfilerCallback:: RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="7745b-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="7745b-111">[ICorProfilerCallback:: RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve [ICorProfilerCallback:: RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="7745b-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="7745b-112">[ICorProfilerCallback:: Remotingserverınvocationdöndürüldü](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) ve [ICorProfilerCallback:: RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="7745b-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="7745b-113">Uzaktan iletişim geri çağırmalar ile ilgili aşağıdaki sorunları bilmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="7745b-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="7745b-114">Bir uzaktan iletişim işlevinin yürütülmesi profil oluşturucu API 'SI tarafından yansıtılmadığından, istemciden çağrılan ve sunucuda yürütülen işlevlere yönelik bildirimler düzgün bir şekilde alınmaz.</span><span class="sxs-lookup"><span data-stu-id="7745b-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="7745b-115">Gerçek çağrı bir proxy nesnesi aracılığıyla gerçekleşir; Profil Oluşturucu için, belirli işlevlerin JıT olarak derlendiğini ancak hiç kullanılmayacağını görünür.</span><span class="sxs-lookup"><span data-stu-id="7745b-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="7745b-116">Profil Oluşturucu, zaman uyumsuz uzaktan iletişim olayları için doğru bildirimler almaz.</span><span class="sxs-lookup"><span data-stu-id="7745b-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7745b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7745b-117">Requirements</span></span>  
 <span data-ttu-id="7745b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7745b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7745b-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7745b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7745b-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7745b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7745b-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7745b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7745b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7745b-122">See also</span></span>

- [<span data-ttu-id="7745b-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7745b-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
