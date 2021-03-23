---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeStopSession yöntemi'
title: 'ICorProfilerInfo12:: EventPipeStopSession yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeStopSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c1b104f63755bcec52a113be7e2aa9af76ecd34e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805720"
---
# <a name="icorprofilerinfo12eventpipestopsession-method"></a>ICorProfilerInfo12:: EventPipeStopSession yöntemi

Bir EventPipe oturumunu durdurup gelecekteki olayların oturuma yazılmasını önler.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT EventPipeStopSession(
        [in] EVENTPIPE_SESSION session);
```  
  
## <a name="parameters"></a>Parametreler

`session` 'ndaki Durdurulacak oturumun KIMLIĞI.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 arabirimi](icorprofilerinfo12-interface.md)
