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
ms.openlocfilehash: 64df6a81eb23c20537238c702fd0c204d64d14bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434554"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize Yöntemi
Her yeni ortak dil çalışma zamanı (CLR) uygulaması başlatıldığında kod profil oluşturucuyu başlatmak için çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pICorProfilerInfoUnk`  
 bir [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabirim işaretçisi için profil oluşturucunun sorgulaması [gereken arabirim.](/cpp/atl/iunknown)  
  
## <a name="remarks"></a>Açıklamalar  
 `Initialize` çağrısı, sabit olan geri çağırmaları etkinleştirmek (veya devre dışı bırakmak) için tek fırsattır. `Initialize` çağrısı tarafından bir geri çağırma etkinleştirildikten sonra, [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)kullanılarak daha sonra devre dışı bırakılamaz. [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesinin COR_PRF_MONITOR_IMMUTABLE değeri, hangi olayların sabit olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Shutdown Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
