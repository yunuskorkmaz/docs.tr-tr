---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: Eventpipegetproviderınfo yöntemi'
title: 'ICorProfilerInfo12:: Eventpipegetproviderınfo yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeGetProviderInfo
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7bc7ffe1c31e88dc1c65f1670f9bd179e732abfe
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805707"
---
# <a name="icorprofilerinfo12eventpipegetproviderinfo-method"></a>ICorProfilerInfo12:: Eventpipegetproviderınfo yöntemi

Profil oluşturucunun, diğer EventPipe dinleyicilerinin alması için olayları yazmak üzere kullanabileceği bir EventPipe sağlayıcısı oluşturur.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT EventPipeGetProviderInfo(
                [in] EVENTPIPE_PROVIDER provider,
                [in]  ULONG      cchName,
                [out] ULONG      *pcchName,
                [out, annotation("_Out_writes_to_(cchName, *pcchName)")]
                      WCHAR      providerName[]);
```  
  
## <a name="parameters"></a>Parametreler

`provider` 'ndaki Adına sağlanacak sağlayıcının KIMLIĞI.

`cchName` 'ndaki ' Nin karakter cinsinden boyutu `providerName` .

`pcchName` dışı Toplam karakter uzunluğuna yönelik bir işaretçi `providerName` .

`providerName` dışı Çağıran, geniş karakter arabelleği sağladı. İşlev, arabelleği döndürdüğünde, sağlayıcının adını içerecektir.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [EventPipe genel bakış](../../../core/diagnostics/eventpipe.md)
- [İyi bilinen EventProviders](../../../core/diagnostics/well-known-event-providers.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 arabirimi](icorprofilerinfo12-interface.md)
