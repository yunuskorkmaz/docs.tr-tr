---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeDefineEvent yöntemi'
title: 'ICorProfilerInfo12:: EventPipeDefineEvent yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeDefineEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 845f7f26dce7aa0f4b7d895b9f04cc89e7ac7192
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805759"
---
# <a name="icorprofilerinfo12eventpipedefineevent-method"></a>ICorProfilerInfo12:: EventPipeDefineEvent yöntemi

Mevcut bir sağlayıcıda EventPipe olayını tanımlar. Bu sağlayıcı, diğer dinleyicilerinin alabileceği EventPipe olaylarını yazmak için kullanılabilir.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT EventPipeDefineEvent(
                [in] EVENTPIPE_PROVIDER     provider,
                [in, string] const WCHAR   *eventName,
                [in] UINT32                 eventID,
                [in] UINT64                 keywords,
                [in] UINT32                 eventVersion,
                [in] UINT32                 level,
                [in] UINT8                  opcode,
                [in] BOOL                   needStack,
                [in] UINT32                 cParamDescs,
                [in, size_is(cParamDescs)]
                     COR_PRF_EVENTPIPE_PARAM_DESC pParamDescs[],
                [out] EVENTPIPE_EVENT      *pEvent);
```  
  
## <a name="parameters"></a>Parametreler

`provider` 'ndaki Bir olayın tanımlanacağı sağlayıcının KIMLIĞI.

`eventName` 'ndaki Olay adını içeren, null ile sonlandırılmış geniş bir karakter dizesinin işaretçisi.

`eventID` 'ndaki Tanımlanmakta olan olayın KIMLIĞI.

`keywords` 'ndaki Tanımlanmakta olan olayın anahtar sözcükleri.

`eventVersion` 'ndaki Tanımlanmakta olan olayın sürümü.

`level` 'ndaki Tanımlanmakta olan olayın düzeyi.

`opcode` 'ndaki Tanımlanmakta olan olayın işlem kodu.

`needStack` 'ndaki `BOOL` Bu olay her tetiklendiğinde yönetilen yığınların toplanıp toplanmayacağını belirten bir.

`cParamDescs` 'ndaki İçindeki parametrelerin sayısı `pParamDescs` .

`pParamDescs` 'ndaki `COR_PRF_EVENTPIPE_PARAM_DESC` Tanımlanmakta olan olaya parametre türlerini tanımlayan dizi.

`pEvent` dışı Çağıran, işlev döndürdüğünde tanımlanmakta olan olayın KIMLIĞIYLE doldurulacak bir işaretçi sağladı.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [EventPipe genel bakış](../../../core/diagnostics/eventpipe.md)
- [İyi bilinen EventProviders](../../../core/diagnostics/well-known-event-providers.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 arabirimi](icorprofilerinfo12-interface.md)
- [COR_PRF_EVENTPIPE_PARAM_DESC yapısı](cor-prf-eventpipe-param-desc-structure.md)
