---
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
ms.openlocfilehash: 91fb902aab678e29c6e74380e3576fa5c4ae62d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500907"
---
# <a name="cor_prf_gc_generation_range-structure"></a>COR_PRF_GC_GENERATION_RANGE Yapısı
Çöp toplama işlemi yapılmakta olan belleğin bir aralığını (yani bloğunu) açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 `rangeLength`Değerin yalnızca ICorProfilerInfo2:: GarbageCollectionStarted veya ICorProfilerCallback2:: GarbageCollectionFinished yönteminden çağrılan, [:: Getgenerationlimiti](icorprofilerinfo2-getgenerationbounds-method.md) veya [ICorProfilerInfo2:: GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), her ikisi de olan `COR_PRF_GC_GENERATION_RANGE` . [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](profiling-structures.md)
