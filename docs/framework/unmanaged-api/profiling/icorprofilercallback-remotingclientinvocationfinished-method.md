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
ms.openlocfilehash: f5786db1f17e8a463dc78f9c93464145be3a8f32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499993"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a>ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi
Bir uzaktan iletişim çağrısının istemci üzerinde tamamlanmasının çalıştırıldığı profil oluşturucuyu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Uzaktan iletişim çağrısı zaman uyumlu ise, sunucuda tamamlanmayı da çalıştırmıştır. Uzaktan iletişim çağrısı zaman uyumsuz ise, çağrı işlendiği zaman yanıt beklenmeye devam edebilir. Bir yanıt bekleniyorsa, [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) çağrısı ve bir `RemotingClientInvocationFinished` zaman uyumsuz çağrının gerekli ikincil işlemesini göstermek için ek bir çağrı olarak gerçekleşir.  
  
 Aşağıdaki geri arama çiftlerinin her biri aynı iş parçacığında gerçekleşir:  
  
- `RemotingClientInvocationStarted`ve [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)  
  
- [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) ve [ICorProfilerCallback:: RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
- [ICorProfilerCallback:: Remotingserverınvocationdöndürüldü](icorprofilercallback-remotingserverinvocationreturned-method.md) ve [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)  
  
 Uzaktan iletişim geri çağırmalar ile ilgili aşağıdaki sorunları bilmelisiniz:  
  
- Bir uzaktan iletişim işlevinin yürütülmesi profil oluşturucu API 'SI tarafından yansıtılmadığından, istemciden çağrılan ve sunucuda yürütülen işlevlere yönelik bildirimler düzgün bir şekilde alınmaz. Gerçek çağrı bir proxy nesnesi aracılığıyla gerçekleşir; Profil Oluşturucu için, belirli işlevlerin JıT olarak derlendiğini ancak hiç kullanılmayacağını görünür.  
  
- Profil Oluşturucu, zaman uyumsuz uzaktan iletişim olayları için doğru bildirimler almaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
