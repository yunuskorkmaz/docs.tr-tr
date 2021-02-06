---
description: 'Daha fazla bilgi edinin: COR_PRF_GC_GENERATION_RANGE yapısı'
title: COR_PRF_GC_GENERATION_RANGE Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: ea67a6e6b972b9406b84ad331e8af6189327c5ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648928"
---
# <a name="cor_prf_gc_generation_range-structure"></a>COR_PRF_GC_GENERATION_RANGE Yapısı

Çöp toplama işlemi yapılmakta olan belleğin bir aralığını (yani bloğunu) açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`generation`|Bellek bloğunun ait olduğu üretimi belirten [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) numaralandırması değeri.|  
|`rangeStart`|Bellek bloğunun başlangıç konumunu belirten nesnenin KIMLIĞI.|  
|`rangeLength`|Bellek bloğunun kullanılan kısmının boyutunu belirten tamsayı işaretçisi (yani, blok içinde kullanılan bellek miktarı).|  
|`rangeLengthReserved`|Bellek bloğunun boyutunu belirten bir tamsayı işaretçisi (yani, blok için ayrılan bellek miktarı).|  
  
## <a name="remarks"></a>Açıklamalar  

 `rangeLength`Değerin yalnızca ICorProfilerInfo2:: GarbageCollectionStarted veya ICorProfilerCallback2:: GarbageCollectionFinished yönteminden çağrılan, [:: Getgenerationlimiti](icorprofilerinfo2-getgenerationbounds-method.md) veya [ICorProfilerInfo2:: GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), her ikisi de olan `COR_PRF_GC_GENERATION_RANGE` . [](icorprofilercallback2-garbagecollectionstarted-method.md) [](icorprofilercallback2-garbagecollectionfinished-method.md)  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](profiling-structures.md)
