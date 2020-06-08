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
ms.openlocfilehash: 79e54cde8757bbe690f9b7c4344a2a3cb19cf627
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499408"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 Yöntemi
Bir sıkıştırma atık toplama işleminin sonucu olarak yığında nesnelerin yeni yerleşimini raporlamak için çağırılır. Profil Oluşturucu [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulamışsa, bu yöntem çağrılır. Bu geri çağırma [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) yönteminin yerini alır, çünkü uzunluklarda neyin ifade edileceği daha büyük nesneler raporlayabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cMovedObjectIDRanges`  
 'ndaki Sıkıştırma atık toplamanın sonucu olarak taşınan bitişik nesne bloklarının sayısı. Diğer bir deyişle, değeri `cMovedObjectIDRanges` `oldObjectIDRangeStart` ,, `newObjectIDRangeStart` ve dizilerinin toplam boyutudur `cObjectIDRangeLength` .  
  
 Sonraki üç bağımsız değişkeni `MovedReferences2` paralel dizilerdir. Diğer bir deyişle, `oldObjectIDRangeStart[i]` , `newObjectIDRangeStart[i]` ve `cObjectIDRangeLength[i]` hepsi bitişik nesnelerin tek bir bloğuna sorun.  
  
 `oldObjectIDRangeStart`  
 'ndaki `ObjectID`Her biri, bellekte bir bitişik ve canlı nesneler bloğunun başlangıç adresi olan, her biri eski (çöp önden koleksiyon) olan bir değerler dizisi.  
  
 `newObjectIDRangeStart`  
 'ndaki `ObjectID`Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan yeni (çöp sonrası koleksiyon) olan bir değer dizisidir.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bir bitişik nesne bloğunun boyutu olan tamsayılar dizisi.  
  
 Ve dizilerinde başvurulan her bir blok için bir boyut belirtilir `oldObjectIDRangeStart` `newObjectIDRangeStart` .  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sıkıştırma atık toplayıcısı, ölü nesneler tarafından kullanılan belleği geri kazanır ve serbest bırakılan alanı sıkıştırır. Sonuç olarak, canlı nesneler yığın içinde taşınabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerler değişebilir.  
  
 Var olan bir `ObjectID` değerin ( `oldObjectID` ) aşağıdaki aralıkta olduğunu varsayın:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Bu durumda, aralığın başlangıcından nesnenin başlangıcına kadar olan fark aşağıdaki gibidir:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Aşağıdaki aralıkta olan herhangi bir değeri için `i` :  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 Yeni ' ni `ObjectID` aşağıda gösterildiği gibi hesaplayabilirsiniz:  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )  
  
 Hiçbir değerin hiçbiri `ObjectID` `MovedReferences2` geri çağırma sırasında geçerli değildir çünkü çöp toplayıcı nesneleri eski konumlardan yeni konumlara taşıma işleminin ortasında olabilir. Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `MovedReferences2` . [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması, tüm nesnelerin yeni konumlarına taşındığını ve incelemesinin gerçekleştirilebileceğini gösterir.  
  
 Profiler hem [ICorProfilerCallback](icorprofilercallback-interface.md) hem de [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimlerini uygularsa, `MovedReferences2` yöntemi [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) yönteminden önce çağrılır, ancak yalnızca `MovedReferences2` Yöntem başarıyla döndürülür. Profil oluşturucular `MovedReferences2` , ikinci yöntemi çağırmayı önlemek için yöntemden hata olduğunu gösteren BIR hresult döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [MovedReferences Yöntemi](icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
