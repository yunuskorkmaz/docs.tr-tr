---
title: COR_PRF_GC_ROOT_KIND Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: 0ea584bfff4340e5e9635d6c31e177e88765b582
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500877"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a>COR_PRF_GC_ROOT_KIND Numaralandırması
[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplama kökünün türünü gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|Kök, yığındaki bir değişkendir.|  
|`COR_PRF_GC_ROOT_FINALIZER`|Kök, Sonlandırıcı sırasındaki bir giriştir.|  
|`COR_PRF_GC_ROOT_HANDLE`|Kök bir atık toplama tanıtıcıdır.|  
|`COR_PRF_GC_ROOT_OTHER`|Kök türü belirtilmemiş.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
