---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo12 Interface'
title: ICorProfilerInfo12 arabirimi
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a8b91eba686478c3e825ae15d6ae95bd0ffad944
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805733"
---
# <a name="icorprofilerinfo12-interface"></a>ICorProfilerInfo12 arabirimi

 EventPipe oturumları, olayları ve sağlayıcıları oluşturmak için yöntemler sağlayan [ICorProfilerInfo11](icorprofilerinfo11-interface.md) öğesinin bir alt sınıfı.
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EventPipeStartSession yöntemi](icorprofilerinfo12-eventpipestartsession-method.md)|Profil Oluşturucu EventPipe oturumu başlatır.|
|[EventPipeAddProviderToSession yöntemi](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)|Mevcut bir EventPipe oturumuna bir sağlayıcı ekler.|
|[EventPipeStopSession yöntemi](icorprofilerinfo12-eventpipestopsession-method.md)|Bir EventPipe oturumunu sonlandırır.|
|[EventPipeCreateProvider yöntemi](icorprofilerinfo12-eventpipecreateprovider-method.md)|Bir EventPipe sağlayıcısı oluşturur.|  
|[Eventpipegetproviderınfo yöntemi](icorprofilerinfo12-eventpipegetproviderinfo-method.md)|Bir EventPipe sağlayıcısının adını KIMLIĞINDEN alır.|
|[EventPipeDefineEvent yöntemi](icorprofilerinfo12-eventpipedefineevent-method.md)|Mevcut bir EventPipe sağlayıcısında bir olayı tanımlar.|  
|[EventPipeWriteEvent yöntemi](icorprofilerinfo12-eventpipewriteevent-method.md)|Bir EventPipe olayı yazar.|
  
## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [EventPipe genel bakış](../../../core/diagnostics/eventpipe.md)
- [İyi bilinen EventProviders](../../../core/diagnostics/well-known-event-providers.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
