---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback10:: Eventpipeeventteslim edildi yöntemi'
title: 'ICorProfilerCallback10:: Eventpipeeventteslim edildi yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeEventDelivered
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7b2ca813d610c2b41d97d8cd76dac22ca38802d7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805642"
---
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a>ICorProfilerCallback10:: Eventpipeeventteslim edildi yöntemi

Profiler 'ın Şu anda etkin oturumuna her bir EventPipe olayı teslim edildiğinde profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT EventPipeEventDelivered(
        [in] EVENTPIPE_PROVIDER provider,
        [in] DWORD eventId,
        [in] DWORD eventVersion,
        [in] ULONG cbMetadataBlob,
        [in, size_is(cbMetadataBlob)] LPCBYTE metadataBlob,
        [in] ULONG cbEventData,
        [in, size_is(cbEventData)] LPCBYTE eventData,
        [in] LPCGUID pActivityId,
        [in] LPCGUID pRelatedActivityId,
        [in] ThreadID eventThread,
        [in] ULONG numStackFrames,
        [in, length_is(numStackFrames)] UINT_PTR stackFrames[]); 
```  
  
## <a name="parameters"></a>Parametreler

`provider` 'ndaki Bu olayın kaynaklandığı sağlayıcı.

`eventId` 'ndaki Teslim edilen olayın KIMLIĞI.

`eventVersion` 'ndaki Teslim edilen etkinliğin sürümü.

`cbMetadataBlob` 'ndaki Bayt cinsinden uzunluğu `metadataBlob` .

`metadataBlob` 'ndaki Olay için meta veri blobu işaretçisi.

`cbEventData` 'ndaki Bayt cinsinden uzunluğu `eventData` .

`eventData` 'ndaki Olay için yük.

`pActivityId` 'ndaki Olayın etkinlik KIMLIĞINI veya NULL değerini temsil eden GUID işaretçisi.

`pRelatedActivityId` 'ndaki Olayın ilgili etkinlik KIMLIĞINI veya NULL değerini temsil eden GUID işaretçisi.

`eventThread` 'ndaki Olayın gerçekleştiği iş parçacığının KIMLIĞI.

`numStackFrames` 'ndaki Dizideki öğelerin sayısı `stackFrames` .

`stackFrames` 'ndaki Etkinliğin yönetilen çağrı yığınını temsil eden kod adresleri dizisi.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 arabirimi](icorprofilerinfo12-interface.md)
- [ICorProfilerInfo12. EventPipeStartSession yöntemi](icorprofilerinfo12-eventpipestartsession-method.md)
