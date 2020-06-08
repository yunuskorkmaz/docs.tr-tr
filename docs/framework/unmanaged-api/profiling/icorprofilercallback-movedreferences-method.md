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
ms.openlocfilehash: 1214182c95f7d0304ec920a2ea7dae91b1f4a790
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503347"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences Yöntemi
Bir sıkıştırma atık toplama işleminin sonucu olarak yığında nesnelerin yeni yerleşimini raporlamak için çağırılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cMovedObjectIDRanges`  
 'ndaki Sıkıştırma atık toplamanın sonucu olarak taşınan bitişik nesne bloklarının sayısı. Diğer bir deyişle, değeri `cMovedObjectIDRanges` `oldObjectIDRangeStart` ,, `newObjectIDRangeStart` ve dizilerinin toplam boyutudur `cObjectIDRangeLength` .  
  
 Sonraki üç bağımsız değişkeni `MovedReferences` paralel dizilerdir. Diğer bir deyişle, `oldObjectIDRangeStart[i]` , `newObjectIDRangeStart[i]` ve `cObjectIDRangeLength[i]` hepsi bitişik nesnelerin tek bir bloğuna sorun.  
  
 `oldObjectIDRangeStart`  
 'ndaki `ObjectID`Her biri, bellekte bir bitişik ve canlı nesneler bloğunun başlangıç adresi olan, her biri eski (çöp önden koleksiyon) olan bir değerler dizisi.  
  
 `newObjectIDRangeStart`  
 'ndaki `ObjectID`Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan yeni (çöp sonrası koleksiyon) olan bir değer dizisidir.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bir bitişik nesne bloğunun boyutu olan tamsayılar dizisi.  
  
 Ve dizilerinde başvurulan her bir blok için bir boyut belirtilir `oldObjectIDRangeStart` `newObjectIDRangeStart` .  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bu yöntem `MAX_ULONG` , 64-bit platformlarda 4 GB 'den büyük nesneler için boyutları raporlar. 4 GB 'den büyük nesnelerin boyutunu almak için, bunun yerine [ICorProfilerCallback4:: MovedReferences2](icorprofilercallback4-movedreferences2-method.md) metodunu kullanın.  
  
 Bir sıkıştırma atık toplayıcısı, ölü nesneler tarafından kullanılan belleği geri kazanır ve serbest bırakılan alanı sıkıştırır. Sonuç olarak, canlı nesneler yığın içinde taşınabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerler değişebilir.  
  
 Var olan bir `ObjectID` değerin ( `oldObjectID` ) aşağıdaki aralıkta olduğunu varsayın:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Bu durumda, aralığın başlangıcından nesnenin başlangıcına kadar olan fark aşağıdaki gibidir:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Aşağıdaki aralıkta olan herhangi bir değeri için `i` :  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 Yeni ' ni `ObjectID` aşağıda gösterildiği gibi hesaplayabilirsiniz:  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )  
  
 `ObjectID` `MovedReferences` Çöp toplama nesneleri eski konumlardan yeni konumlara taşıma işleminin ortasında olabileceğinden, tarafından geçirilen değerlerin hiçbiri geri çağırma sırasında geçerli değildir. Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `MovedReferences` . [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması, tüm nesnelerin yeni konumlarına taşındığını ve incelemesinin gerçekleştirilebileceğini gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [MovedReferences2 Yöntemi](icorprofilercallback4-movedreferences2-method.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
