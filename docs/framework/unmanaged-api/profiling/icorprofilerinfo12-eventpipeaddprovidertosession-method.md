---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeAddProviderToSession yöntemi'
title: 'ICorProfilerInfo12:: EventPipeAddProviderToSession yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeAddProviderToSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 70654660c496211c20459ef9ba37dfbd96b829b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805694"
---
# <a name="icorprofilerinfo12eventpipeaddprovidertosession-method"></a>ICorProfilerInfo12:: EventPipeAddProviderToSession yöntemi

Mevcut bir EventPipe oturumuna bir sağlayıcı ekler.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT EventPipeAddProviderToSession(
        [in] EVENTPIPE_SESSION                 session,
        [in] COR_PRF_EVENTPIPE_PROVIDER_CONFIG providerConfig);
```  
  
## <a name="parameters"></a>Parametreler

`session` 'ndaki Sağlayıcının ekleneceği oturumun KIMLIĞI.

`providerConfig` 'ndaki `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` Oturuma eklenecek sağlayıcıyı açıklayan bir sağlayıcı.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).
**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [EventPipe genel bakış](../../../core/diagnostics/eventpipe.md)
- [İyi bilinen EventProviders](../../../core/diagnostics/well-known-event-providers.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback10 arabirimi](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 arabirimi](icorprofilerinfo12-interface.md)
- [COR_PRF_EVENTPIPE_PROVIDER_CONFIG yapısı](cor-prf-eventpipe-provider-config-structure.md)
