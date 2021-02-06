---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_GC_ROOT_FLAGS numaralandırması'
title: COR_PRF_GC_ROOT_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 6d566ed5ac1d0b4e15a855fbbb8a0fca3a5a429e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648824"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS Numaralandırması

Çöp toplama kökünün bir özelliğini gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|Kök bir çöp toplamanın nesneyi taşımasını engeller.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Kök çöp toplamayı engellemez.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Kök nesnenin kendisi yerine nesnesinin bir alanına başvurur.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Nesnenin başvuru sayısı belirli bir değer ise, kök çöp toplamayı önler.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_PRF_GC_ROOT_FLAGS` Özel köklerle ilgili ek bilgi sağlayan bir bit dır. Ancak, tüm kökler özel değildir. Örneğin, bazı köklere zayıf başvurular, iç işaretçiler, sabitlenmiş veya başvuru sayılır. Bu tür kökler için, iletmek üzere bayrak yoktur. Bu nedenle, [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) yöntemi gibi bu numaralandırmayı kullanan Yöntemler, bayraklar bit maskesi için 0 gönderir ve tüm bayrakların kapalı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
