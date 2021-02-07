---
description: ': ICorProfilerCallback:: Initialize yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b3ff579dee384b331450aa54aace39890febfe30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705947"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize Yöntemi

Her yeni ortak dil çalışma zamanı (CLR) uygulaması başlatıldığında kod profil oluşturucuyu başlatmak için çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parametreler

- `pICorProfilerInfoUnk`

  \[' in] bir [ICorProfilerInfo](icorprofilerinfo-interface.md) arabirim işaretçisi için sorgu gereken bir [IUnknown](/cpp/atl/iunknown) arabirimine yönelik işaretçi.  

## <a name="remarks"></a>Açıklamalar  

 `Initialize`Çağrı, sabit olan geri çağırmaları etkinleştirmek (veya devre dışı bırakmak) için tek fırsattır. Çağrı tarafından bir geri çağırma etkinleştirildikten sonra `Initialize` [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)kullanılarak daha sonra devre dışı bırakılamaz. [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) sabit listesinin COR_PRF_MONITOR_IMMUTABLE değeri, hangi olayların sabit olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [Shutdown Yöntemi](icorprofilercallback-shutdown-method.md)
