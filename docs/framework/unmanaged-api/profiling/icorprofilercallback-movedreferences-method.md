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
ms.openlocfilehash: 28fa18535cce50a62f6aca7ae6f013628698c6dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences Yöntemi
Yeni düzenini sıkıştırma çöp toplama sonucunda yığınındaki nesnelerin bildirmek için çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cMovedObjectIDRanges`  
 [in] Sıkıştırma atık toplama sonucu olarak taşınmış bitişik nesnelerin bloğu sayısı. Diğer bir deyişle, değeri `cMovedObjectIDRanges` toplam boyutu `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizileri.  
  
 Sonraki üç bağımsız değişkenleri `MovedReferences` paralel dizidir. Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, ve `cObjectIDRangeLength[i]` tüm bitişik nesnelerinin tek bir blok ilgilendiren.  
  
 `oldObjectIDRangeStart`  
 [in] Bir dizi `ObjectID` her biri başlangıç adresi bloğunun bitişik eski (ön çöp toplama) olduğunda, değerleri, bellekte nesneleri canlı.  
  
 `newObjectIDRangeStart`  
 [in] Bir dizi `ObjectID` her biri yeni (sonrası çöp toplama) başlangıç adresi bloğunun bitişik olduğunda, değerleri, bellekte nesneleri canlı.  
  
 `cObjectIDRangeLength`  
 [in] Her biri bir blok bellekte bitişik nesnelerin boyutudur dizisi.  
  
 Başvuru her blok için belirtilen bir boyutu `oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bu yöntem olarak boyutlarını raporlar `MAX_ULONG` 64 bit platformlarda 4 GB'den büyük nesneler için. 4 GB'den büyük nesneleri boyutunu almak için [Icorprofilercallback4::movedreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yöntemi yerine.  
  
 Sıkıştırma atık toplayıcı ölü nesneleri ve alan serbest sıkıştırır tarafından kapladığı bellek geri kazanır. Sonuç olarak, dinamik nesneler yığında taşınmış olabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerleri değişebilir.  
  
 Varsayımında varolan `ObjectID` değeri (`oldObjectID`) aşağıdaki aralık içinde yer:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Bu durumda, aralığın başlangıç uzaklığı nesneyi başlatmak için aşağıdaki gibidir:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Herhangi bir değer için `i` aşağıdaki aralıkta değil:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Yeni hesaplayabilirsiniz `ObjectID` gibi:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Hiçbiri `ObjectID` geçirilen değerlerinin `MovedReferences` çöp toplama için yeni konumlar eski konumlardan nesneleri taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerlidir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `MovedReferences` çağırın. A [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırma gösteren tüm nesneleri yeni konumlarına taşınmıştır ve İnceleme gerçekleştirilebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [MovedReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
