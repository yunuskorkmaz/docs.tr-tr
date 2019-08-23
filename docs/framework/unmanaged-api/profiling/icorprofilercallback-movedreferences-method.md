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
ms.openlocfilehash: f86c4388fd633c72e846c227d45eff09bb66cf44
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951115"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences Yöntemi
Bir sıkıştırma atık toplama işleminin sonucu olarak yığında nesnelerin yeni yerleşimini raporlamak için çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cMovedObjectIDRanges`  
 'ndaki Sıkıştırma atık toplamanın sonucu olarak taşınan bitişik nesne bloklarının sayısı. Diğer `cMovedObjectIDRanges` bir deyişle, değeri `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizilerinin toplam boyutudur.  
  
 Sonraki üç bağımsız değişkeni `MovedReferences` paralel dizilerdir. Diğer bir deyişle `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]`,, ve `cObjectIDRangeLength[i]` hepsi bitişik nesnelerin tek bir bloğuna sorun.  
  
 `oldObjectIDRangeStart`  
 'ndaki Her biri, `ObjectID` bellekte bir bitişik ve canlı nesneler bloğunun başlangıç adresi olan, her biri eski (çöp önden koleksiyon) olan bir değerler dizisi.  
  
 `newObjectIDRangeStart`  
 'ndaki Her biri, `ObjectID` bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan yeni (çöp sonrası koleksiyon) olan bir değer dizisidir.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bir bitişik nesne bloğunun boyutu olan tamsayılar dizisi.  
  
 `oldObjectIDRangeStart` Ve`newObjectIDRangeStart` dizilerinde başvurulan her bir blok için bir boyut belirtilir.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bu yöntem, 64- `MAX_ULONG` bit platformlarda 4 GB 'den büyük nesneler için boyutları raporlar. 4 GB 'den büyük nesnelerin boyutunu almak için, bunun yerine [ICorProfilerCallback4:: MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metodunu kullanın.  
  
 Bir sıkıştırma atık toplayıcısı, ölü nesneler tarafından kullanılan belleği geri kazanır ve serbest bırakılan alanı sıkıştırır. Sonuç olarak, canlı nesneler yığın içinde taşınabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerler değişebilir.  
  
 Var olan `ObjectID` bir değerin (`oldObjectID`) aşağıdaki aralıkta olduğunu varsayın:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Bu durumda, aralığın başlangıcından nesnenin başlangıcına kadar olan fark aşağıdaki gibidir:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Aşağıdaki aralıkta `i` olan herhangi bir değeri için:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Yeni ' ni `ObjectID` aşağıda gösterildiği gibi hesaplayabilirsiniz:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Çöp toplama nesneleri eski konumlardan yeni `MovedReferences` konumlara taşıma işleminin ortasında olabileceğinden, tarafından geçirilen değerlerinhiçbirigeriçağırmasırasındageçerlideğildir.`ObjectID` Bu nedenle, profil oluşturucular bir `MovedReferences` çağrı sırasında nesneleri incelemeyi denememelidir. [ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması, tüm nesnelerin yeni konumlarına taşındığını ve incelemesinin gerçekleştirilebileceğini gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
