---
title: ICorProfilerCallback::MovedReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4611b8c186e0293dae73cee4f9d845bb44c167c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073552"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences Yöntemi
Yeni düzen sıkıştırma çöp toplama sonucu olarak yığındaki nesnelerin bildirmek için çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cMovedObjectIDRanges`  
 [in] Taşınabilir sıkıştırma çöp toplama işleminin sonucu olarak, bitişik nesnelerin blokların sayısı. Diğer bir deyişle, değerini `cMovedObjectIDRanges` toplam boyutu `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizileri.  
  
 Sonraki üç bağımsız değişkenleri `MovedReferences` paralel dizidir. Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, ve `cObjectIDRangeLength[i]` tüm bitişik nesnelerinin tek bir blok ilgilendiriyor.  
  
 `oldObjectIDRangeStart`  
 [in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik eski (ön çöp toplamada) olduğunda, değerleri, Canlı nesneleri bellekte.  
  
 `newObjectIDRangeStart`  
 [in] Bir dizi `ObjectID` her biri yeni (sonrası çöp toplamada) başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.  
  
 `cObjectIDRangeLength`  
 [in] Her biri bellekte bitişik nesnelerin bir blok boyutu olan bir tamsayı dizisi.  
  
 Başvurulduğundan her blok için belirtilen bir boyutu `oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bu yöntem boyutları olarak raporlar `MAX_ULONG` 64-bit platformlarda 4 GB'den büyük olan nesneler için. 4 GB'den daha büyük nesnelerin boyutunu almak için kullanın [Icorprofilercallback4::movedreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yöntemi yerine.  
  
 Sıkıştırma atık Toplayıcıya alanı boşaltılana sıkıştırır ve ölü nesneleri ile kapladığı belleği geri kazanır. Sonuç olarak, Canlı nesneler yığında taşınmış olabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerleri değişebilir.  
  
 Varsayımında varolan `ObjectID` değeri (`oldObjectID`) aşağıdaki aralığında yer:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Bu durumda, nesnenin başlangıç aralığın başından uzaklık şu şekilde olur:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 İçin herhangi bir değerini `i` aşağıdaki aralığında olan:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Yeni hesaplayabilirsiniz `ObjectID` gibi:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Hiçbiri `ObjectID` geçirilen değerler `MovedReferences` geri çağırma sırasındaki kendisi, çöp toplama nesneleri eski konumlardan yeni konumlara taşımak ortasında olabileceği için geçerlidir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `MovedReferences` çağırın. A [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) tüm nesnelerin yeni konumlarına taşınmıştır ve İnceleme gerçekleştirilebilir geri çağırma işlemini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
