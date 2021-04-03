---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback10:: EventPipeProviderCreated yöntemi'
title: 'ICorProfilerCallback10:: EventPipeProviderCreated yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeProviderCreated
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 6ce96bf301f1c559923df64edd9dd214c28db918
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231316"
---
# <a name="icorprofilercallback10eventpipeprovidercreated-method"></a>ICorProfilerCallback10:: EventPipeProviderCreated yöntemi

Bir EventPipe sağlayıcısı oluşturulduğunda profil oluşturucuyu bilgilendirir.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT EventPipeProviderCreated([in] EVENTPIPE_PROVIDER provider);
```  
  
## <a name="parameters"></a>Parametreler

`provider` 'ndaki Oluşturulan sağlayıcı.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 arabirimi](icorprofilerinfo12-interface.md)
- [ICorProfilerInfo12. EventPipeAddProviderToSession yöntemi](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
