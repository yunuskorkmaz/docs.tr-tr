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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206583"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a>ICorProfilerCallback::RemotingClientInvocationFinished Yöntemi
Profil Oluşturucu bir çağrının sürebileceği istemcide tamamlanmak üzere çalıştırılmasını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Uzaktan iletişim çağrısı, zaman uyumlu ise, bunu tamamlanana kadar sunucuda çalıştırıldı. Zaman uyumsuz bir çağrının sürebileceği olduysa, çağrı işlendiğinde yanıt hala beklenebilir. Bir yanıt bekleniyorsa, bir çağrı olarak ortaya çıkar [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve ek bir arama `RemotingClientInvocationFinished` zaman uyumsuz bir çağrı gerekli ikincil işlenmesini belirtmek için.  
  
 Her biri aşağıdaki geri çağırmalar çiftleri aynı iş parçacığında ortaya çıkar:  
  
-   `RemotingClientInvocationStarted` ve [Icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
-   [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) ve [Icorprofilercallback::remotingclientınvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
-   [Icorprofilercallback::remotingserverınvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) ve [Icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 Uzaktan iletişimini geri çağırmaları ile ilgili aşağıdaki sorunları farkında olmalıdır:  
  
-   İstemciden çağrılan ve sunucu üzerinde yürütülen işlevler için bildirimler düzgün alınmadı şekilde profil oluşturucu API, uzak bir işlevin yürütülmesini yansıtılmaz. Gerçek çağrısını bir proxy nesnesi olur; Profil Oluşturucu için bazı işlevlerini JIT olarak derlenmiş ancak hiçbir zaman kullanılan görünür.  
  
-   Profil Oluşturucu, zaman uyumsuz uzaktan iletişim olayları için doğru bildirimleri almaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
