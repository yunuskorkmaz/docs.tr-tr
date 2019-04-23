---
title: ICorProfilerCallback4::MovedReferences2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d368c88503853d0620f28f02f88a6d887c1aa681
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156409"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 Yöntemi
Yeni düzen sıkıştırma çöp toplama sonucu olarak yığındaki nesnelerin bildirmek için çağrılır. Profil Oluşturucu uygulanırsa, bu yöntem çağrılır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi. Bu geri çağırma değiştirir [Icorprofilercallback::movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yöntemi, daha büyük olan uzunluğu aşan bir ULONG ifade edilebilir nesne aralıklarını rapor edebilirsiniz çünkü.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cMovedObjectIDRanges`  
 [in] Taşınabilir sıkıştırma çöp toplama işleminin sonucu olarak, bitişik nesnelerin blokların sayısı. Diğer bir deyişle, değerini `cMovedObjectIDRanges` toplam boyutu `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizileri.  
  
 Sonraki üç bağımsız değişkenleri `MovedReferences2` paralel dizidir. Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, ve `cObjectIDRangeLength[i]` tüm bitişik nesnelerinin tek bir blok ilgilendiriyor.  
  
 `oldObjectIDRangeStart`  
 [in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik eski (ön çöp toplamada) olduğunda, değerleri, Canlı nesneleri bellekte.  
  
 `newObjectIDRangeStart`  
 [in] Bir dizi `ObjectID` her biri yeni (sonrası çöp toplamada) başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.  
  
 `cObjectIDRangeLength`  
 [in] Her biri bellekte bitişik nesnelerin bir blok boyutu olan bir tamsayı dizisi.  
  
 Başvurulduğundan her blok için belirtilen bir boyutu `oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri.  
  
## <a name="remarks"></a>Açıklamalar  
 Sıkıştırma atık Toplayıcıya alanı boşaltılana sıkıştırır ve ölü nesneleri ile kapladığı belleği geri kazanır. Sonuç olarak, Canlı nesneler yığında taşınmış olabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerleri değişebilir.  
  
 Varsayımında varolan `ObjectID` değeri (`oldObjectID`) aşağıdaki aralığında yer:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Bu durumda, nesnenin başlangıç aralığın başından uzaklık şu şekilde olur:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 İçin herhangi bir değerini `i` aşağıdaki aralığında olan:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Yeni hesaplayabilirsiniz `ObjectID` gibi:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Hiçbiri `ObjectID` geçirilen değerler `MovedReferences2` geri çağırma sırasındaki kendisi, çöp toplayıcının nesneleri eski konumlardan yeni konumlara taşımak ortasında olabileceğinden geçerlidir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `MovedReferences2` çağırın. A [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) tüm nesnelerin yeni konumlarına taşınmıştır ve İnceleme gerçekleştirilebilir geri çağırma işlemini belirtir.  
  
 Profil Oluşturucu hem de uyguluyorsa [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimleri `MovedReferences2` önce yöntemi çağrıldığında [Icorprofilercallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yöntemi, ancak yalnızca `MovedReferences2` yöntemi başarıyla döndürür. Profil oluşturucular hatasından gösteren HRESULT döndürebilir `MovedReferences2` ikinci yöntem çağırma önlemek için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
