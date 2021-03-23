---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeWriteEvent yöntemi'
title: 'ICorProfilerInfo12:: EventPipeWriteEvent yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeWriteEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a0a06ff0fa1c936518586834f4dfc73810ef0e44
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805746"
---
# <a name="icorprofilerinfo12eventpipewriteevent-method"></a>ICorProfilerInfo12:: EventPipeWriteEvent yöntemi

Bu olayı etkinleştiren tüm dinleyicilerine bir EventPipe olayı yazar.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT EventPipeWriteEvent(
                [in] EVENTPIPE_EVENT    event,
                [in] UINT32             cData,
                [in, size_is(cData)]
                     COR_PRF_EVENT_DATA data[],
                [in] LPCGUID            pActivityId,
                [in] LPCGUID            pRelatedActivityId);
```  
  
## <a name="parameters"></a>Parametreler

`event` 'ndaki Yazılmakta olan olayın KIMLIĞI.

`cData` 'ndaki İçindeki öğe sayısı `data` .

`data` 'ndaki `COR_PRF_EVENT_DATA` Olay bağımsız değişkenlerini içeren bir dizi.

`pActivityId` 'ndaki Olayın etkinlik KIMLIĞINI belirten bir GUID işaretçisi.

`pRelatedActivityId` 'ndaki Olayın ilgili etkinlik KIMLIĞINI belirten bir GUID işaretçisi.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 arabirimi](icorprofilerinfo12-interface.md)
- [COR_PRF_EVENT_DATA yapısı](cor-prf-event-data-structure.md)
