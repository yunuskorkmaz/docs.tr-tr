---
title: ICorProfilerCallback::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e50421dc15dd30f1811dbe5ebef2ff2f7a0a9483
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755829"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize Yöntemi
Yeni bir ortak dil çalışma zamanı (CLR) uygulama başlatıldığında, kod profil oluşturucuyu başlatmak üzere çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pICorProfilerInfoUnk`  
 [içinde](/cpp/atl/iunknown) profil oluşturucu için faydalanacaksa arabirimi bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabirim işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `Initialize` Sabittir geri çağırmaları etkinleştirmek (veya devre dışı bırakmak) yalnızca fırsat çağrıdır. Bir geri çağırma tarafından etkinleştirildikten sonra `Initialize` çağrısı, bunu daha sonra kullanarak devre dışı bırakılamaz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). COR_PRF_MONITOR_IMMUTABLE değerini [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırma belirten olayları sabittir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Shutdown Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
