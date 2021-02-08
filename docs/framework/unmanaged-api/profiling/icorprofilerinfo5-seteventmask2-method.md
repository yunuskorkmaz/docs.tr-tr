---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo5:: SetEventMask2 Yöntemi'
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
ms.openlocfilehash: 2928ec408f2fdeb363164530258a3bf5c9719e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799011"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 Yöntemi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Profil oluşturucunun, ortak dil çalışma zamanından (CLR) olay bildirimleri almak istediği olay türlerini belirten bir değer ayarlar. [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yönteminden daha fazla işlevsellik sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwEventsLow`  
 'ndaki Olayların kategorilerini belirten 4 baytlık bir değer. Her bit, farklı bir yetenek, davranış veya olay türünü denetler. Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.  
  
 `dwEventsHigh`  
 'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.  Her bit, farklı bir yetenek, davranış veya olay türünü denetler. Bitleri [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  

 `SetEventMask2`Yöntemi, profil oluşturucunun abone olduğu geri çağırmaları ayarlamak için kullanılır. Genellikle, hangi bitlerin ayarlandığını öğrenmek için [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) yöntemini çağırır, mantıksal veya `pdwEventsLow` değerlerini ve `pdwEventsHigh` ayarlamak istediğiniz yeni bitleri gerçekleştirin ve sonra `SetEventMask2` yöntemi çağırın.  
  
 Bu yöntem, [SetEventMask](icorprofilerinfo-seteventmask-method.md) yönteminin önerilen alternatifidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo5 Arabirimi](icorprofilerinfo5-interface.md)
- [GetEventMask2 Yöntemi](icorprofilerinfo5-geteventmask2-method.md)
