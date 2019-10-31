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
ms.openlocfilehash: 1e1779c0f4f36b2d7b81832bc90cf5aee0b8a7df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130391"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Profil oluşturucunun, ortak dil çalışma zamanından (CLR) olay bildirimleri almak istediği olay türlerini belirten bir değer ayarlar. [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yönteminden daha fazla işlevsellik sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwEventsLow`  
 'ndaki Olayların kategorilerini belirten 4 baytlık bir değer. Her bit, farklı bir yetenek, davranış veya olay türünü denetler. Bitleri [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması içinde açıklanmaktadır.  
  
 `dwEventsHigh`  
 'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.  Her bit, farklı bir yetenek, davranış veya olay türünü denetler. Bitleri [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması içinde açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetEventMask2` yöntemi, profil oluşturucunun abone olduğu geri çağırmaları ayarlamak için kullanılır. Genellikle, hangi bitlerin ayarlandığını öğrenmek için [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) yöntemini çağırır, `pdwEventsLow` ve `pdwEventsHigh` değerlerini ve ayarlamak istediğiniz tüm yeni bitleri gerçekleştirin ve ardından `SetEventMask2` yöntemini çağırın.  
  
 Bu yöntem, [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yönteminin önerilen alternatifidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [GetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
