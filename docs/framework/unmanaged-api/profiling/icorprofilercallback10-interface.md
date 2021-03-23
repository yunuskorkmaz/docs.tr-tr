---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback10 Interface'
title: ICorProfilerCallback10 arabirimi
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d9091dc81307e2dcb83e74154a8217dffaa1e7a2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805655"
---
# <a name="icorprofilercallback10-interface"></a>ICorProfilerCallback10 arabirimi

 Profil oluşturucuyu, EventPipe olaylarının Profiler 'ın Şu anda etkin oturumuna teslim edildiğini bildirmek için geri çağırma yöntemleri sağlayan bir [ICorProfilerCallback9](icorprofilercallback9-interface.md) alt sınıfı.
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Eventpipeeventteslim edilen yöntem](icorprofilercallback10-eventpipeeventdelivered-method.md)|Profiler öğesine bir EventPipe olayının, profil oluşturucunun açık olduğu oturuma teslim edildiğini bildirir.|
|[EventPipeProviderCreated yöntemi](icorprofilercallback10-eventpipeprovidercreated-method.md)|Profil oluşturucuya bir EventPipe sağlayıcısının oluşturulduğunu bildirir ve profil oluşturucunun bu sağlayıcıyı oturumlarını eklemesini sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [EventPipe genel bakış](../../../core/diagnostics/eventpipe.md)
- [İyi bilinen EventProviders](../../../core/diagnostics/well-known-event-providers.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo12 arabirimi](ICorProfilerInfo12-interface.md)
- [ICorProfilerInfo12. EventPipeStartSession yöntemi](ICorProfilerInfo12-eventpipestartsession-method.md)
- [ICorProfilerInfo12. EventPipeStopSession yöntemi](ICorProfilerInfo12-eventpipestopsession-method.md)
