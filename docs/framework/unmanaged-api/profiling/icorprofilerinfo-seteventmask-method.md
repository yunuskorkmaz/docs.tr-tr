---
title: ICorProfilerInfo::SetEventMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
ms.openlocfilehash: f7dee16373fc67580130c57482a130ba02f50204
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497471"
---
# <a name="icorprofilerinfoseteventmask-method"></a>ICorProfilerInfo::SetEventMask Yöntemi
Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği olay türlerini belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwEvents`  
 'ndaki Olayların kategorilerini belirten 4 baytlık bir değer. Her bit, farklı bir yetenek, davranış veya olay türünü denetler. Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yerine [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırmanız gerekir. `SetEventMask`Yöntemi desteklenmeye devam etse de, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) ek işlevsellik sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [SetEventMask2 Yöntemi](icorprofilerinfo5-seteventmask2-method.md)
