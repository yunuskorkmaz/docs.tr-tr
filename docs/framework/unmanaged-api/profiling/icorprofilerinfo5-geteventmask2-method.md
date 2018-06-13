---
title: ICorProfilerInfo5::GetEventMask2 Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8973e100694be0f50b575d978f3327b8b3a1d334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455671"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>ICorProfilerInfo5::GetEventMask2 Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Profil Oluşturucu ortak dil çalışma (CLR) bildirimlerini almak istediği geçerli olay kategorileri alır.  Tarafından sağlanmayan işlevsellik sağlar [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwEventsLow`  
 [out] Olayların kategorilerini belirler 4-bayt bir değer için bir işaretçi. Her bitin farklı yetenek, davranış veya olay türünü denetler. BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.  
  
 `pdwEventsHigh`  
 [out] Olayların kategorilerini belirler 4-bayt bir değer için bir işaretçi.  Her bitin farklı yetenek, davranış veya olay türünü denetler. BITS açıklanan [cor_prf_hıgh_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetEventMask2` Yöntemi profil oluşturucu abone için hangi geri aramalar belirlemek için kullanılır. Mantıksal OR, genellikle gerçekleştirdiğiniz `pdwEventsLow` ve `pdwEventsHigh` değerleri ve istediğiniz ayarlayın ve ardından çağırmak için herhangi bir yeni BITS [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.  
  
 Bu yöntem için önerilen alternatiftir [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [SetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
