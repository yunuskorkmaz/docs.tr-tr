---
title: ICorProfilerInfo5::SetEventMask2 Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e1ef960f9c244d257f3c2f30ba60c2f64d1d704
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655705"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Profil Oluşturucu ortak dil çalışma zamanından (CLR) olay bildirimlerini almak istediği olaylara türlerini belirten bir değeri ayarlar. Daha fazla işlevsellik sağlar [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwEventsLow`  
 [in] Olayların kategorilerini belirten bir 4 baytlık değeri. Farklı yetenek, davranış veya olay türü her bit denetler. BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.  
  
 `dwEventsHigh`  
 [in] Olayların kategorilerini belirten bir 4 baytlık değeri.  Farklı yetenek, davranış veya olay türü her bit denetler. BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) sabit listesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetEventMask2` Yöntemi için profil oluşturucu abone geri çağırmaları ayarlamak için kullanılır. Genellikle, arama [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) yöntemi hangi bitlerin ayarlanmış olup, belirlemek için mantıksal OR gerçekleştirmek, `pdwEventsLow` ve `pdwEventsHigh` değerleri ve ayarlayın ve ardından çağırmak için istediğiniz herhangi bir yeni BITS `SetEventMask2` yöntemi.  
  
 Bu yöntem için önerilen alternatiftir [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [GetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
