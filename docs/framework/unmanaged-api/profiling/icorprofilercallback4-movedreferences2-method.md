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
ms.openlocfilehash: 2f305852ae218417aa1f4d4fe9d2076c0163fd60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865278"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 Yöntemi
Bir sıkıştırma atık toplama işleminin sonucu olarak yığında nesnelerin yeni yerleşimini raporlamak için çağırılır. Profil Oluşturucu [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulamışsa, bu yöntem çağrılır. Bu geri çağırma [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) yönteminin yerini alır, çünkü uzunluklarda neyin ifade edileceği daha büyük nesneler raporlayabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cMovedObjectIDRanges`  
 'ndaki Sıkıştırma atık toplamanın sonucu olarak taşınan bitişik nesne bloklarının sayısı. Diğer bir deyişle, `cMovedObjectIDRanges` değeri `oldObjectIDRangeStart`, `newObjectIDRangeStart`ve `cObjectIDRangeLength` dizilerinin toplam boyutudur.  
  
 `MovedReferences2` sonraki üç bağımsız değişkeni paralel dizilerdir. Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`ve `cObjectIDRangeLength[i]` hepsi de tek bir bitişik nesne bloğuna sorun.  
  
 `oldObjectIDRangeStart`  
 'ndaki Her biri, bellekte bulunan bir bitişik ve canlı nesneler bloğunun başlangıç adresi olan `ObjectID` değerlerden oluşan bir dizi.  
  
 `newObjectIDRangeStart`  
 'ndaki Her biri, bellekte bir bitişik ve canlı nesneler bloğunun başlangıç adresinden yeni (çöp sonrası koleksiyon) olan `ObjectID` değerlerden oluşan bir dizi.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bir bitişik nesne bloğunun boyutu olan tamsayılar dizisi.  
  
 `oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri içinde başvurulan her bir blok için bir boyut belirtilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sıkıştırma atık toplayıcısı, ölü nesneler tarafından kullanılan belleği geri kazanır ve serbest bırakılan alanı sıkıştırır. Sonuç olarak, canlı nesneler yığın içinde taşınabilir ve önceki bildirimler tarafından dağıtılan `ObjectID` değerleri değişebilir.  
  
 Mevcut bir `ObjectID` değerinin (`oldObjectID`) aşağıdaki aralıkta olduğunu varsayın:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Bu durumda, aralığın başlangıcından nesnenin başlangıcına kadar olan fark aşağıdaki gibidir:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Aşağıdaki aralıktaki `i` herhangi bir değeri için:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Yeni `ObjectID` aşağıdaki gibi hesaplayabilirsiniz:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Çöp toplayıcı nesneleri eski konumlardan yeni konumlara taşıma işleminin ortasında olabileceğinden, geri çağırma sırasında `MovedReferences2` tarafından geçirilen `ObjectID` değerlerinden hiçbiri geçerli değildir. Bu nedenle, profil oluşturucular `MovedReferences2` çağrısı sırasında nesneleri incelemeyi denememelidir. [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması, tüm nesnelerin yeni konumlarına taşındığını ve incelemesinin gerçekleştirilebileceğini gösterir.  
  
 Profiler hem [ICorProfilerCallback](icorprofilercallback-interface.md) hem de [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimlerini uygularsa, `MovedReferences2` yöntemi [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) yönteminden önce çağrılır, ancak yalnızca `MovedReferences2` yöntemi başarıyla döndürülür. Profil oluşturucular, ikinci yöntemi çağırmayı önlemek için `MovedReferences2` yönteminden hata belirten bir HRESULT döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [MovedReferences Yöntemi](icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
