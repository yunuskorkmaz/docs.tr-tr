---
title: "ICorProfilerInfo5::SetEventMask2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: IcorProfilerInfo5.SetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e53ad9d297656e26f8ba0e9d7669711a3f44ef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Profil Oluşturucu ortak dil çalışma (CLR) olay bildirimlerini almak istediği olay türlerini belirten bir değer ayarlar. Daha fazla işlevsellik sağlar [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwEventsLow`  
 [in] Olayların kategorilerini belirler 4-bayt değeri. Her bitin farklı yetenek, davranış veya olay türünü denetler. BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.  
  
 `dwEventsHigh`  
 [in] Olayların kategorilerini belirler 4-bayt değeri.  Her bitin farklı yetenek, davranış veya olay türünü denetler. BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetEventMask2` Yöntemi için profil oluşturucu abone geri aramalar ayarlamak için kullanılır. Genellikle, arama [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) hangi BITS ayarlanır, belirlemek amacıyla yöntemi gerçekleştirmek, mantıksal veya kendi `pdwEventsLow` ve `pdwEventsHigh` değerleri ve istediğiniz ayarlayın ve ardından çağırmak için herhangi bir yeni BITS `SetEventMask2` yöntemi.  
  
 Bu yöntem için önerilen alternatiftir [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [GetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
