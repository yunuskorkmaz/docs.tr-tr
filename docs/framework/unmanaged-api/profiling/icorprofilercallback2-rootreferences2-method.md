---
title: ICorProfilerCallback2::RootReferences2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: 2ce58113f40c8eb67a89b6ab6c9bb8f755975bd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499759"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 Yöntemi
Çöp toplama gerçekleştirildikten sonra profil oluşturucuyu kök başvuruları hakkında bilgilendirir. Bu yöntem [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) yönteminin bir uzantısıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 'ndaki `rootRefIds`,, `rootKinds` `rootFlags` , Ve `rootIds` dizilerindeki öğelerin sayısı.  
  
 `rootRefIds`  
 'ndaki Her biri bir statik nesneye veya yığında bir nesneye başvuran bir nesne kimlikleri dizisi. `rootKinds`Dizideki öğeler dizideki karşılık gelen öğeleri sınıflandırmak için bilgi sağlar `rootRefIds` .  
  
 `rootKinds`  
 'ndaki Çöp toplama kökünün türünü belirten [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) değerleri dizisi.  
  
 `rootFlags`  
 'ndaki Bir çöp toplama kökünün özelliklerini tanımlayan [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) değerleri dizisi.  
  
 `rootIds`  
 'ndaki Parametrenin değerine bağlı olarak çöp toplama köküyle ilgili ek bilgiler içeren bir tamsayıyı işaret eden UINT_PTR değerleri dizisi `rootKinds` .  
  
 Kök türü bir yığın ise, kök KIMLIĞI değişkeni içeren işleve yöneliktir. Bu kök KIMLIĞI 0 ise, işlev CLR 'ye iç olan adlandırılmamış bir işlevdir. Kök türü bir tanıtıcı ise, kök KIMLIĞI çöp toplama tutamacı içindir. Diğer kök türleri için KIMLIK donuk bir değerdir ve göz ardı edilmelidir.  
  
## <a name="remarks"></a>Açıklamalar  
 `rootRefIds`,, `rootKinds` , `rootFlags` Ve `rootIds` dizileri paralel dizilerdir. ,,, `rootRefIds[i]` `rootKinds[i]` `rootFlags[i]` Ve `rootIds[i]` hepsi aynı köke sahip olur.  
  
 Her ikisi de `RootReferences` `RootReferences2` profil oluşturucuyu bildirmek için çağırılır. Profil oluşturucular, normalde bir yöntemi veya diğerini uygular, ancak geçirilen bilgiler `RootReferences2` geçilen bir üst kümesidir `RootReferences` .  
  
 ' Deki girişlerin `rootRefIds` sıfır olması mümkündür. Bu, karşılık gelen kök başvurusunun null olduğunu ve yönetilen yığında bir nesneye başvurmayacağı anlamına gelir.  
  
 Tarafından döndürülen nesne kimlikleri `RootReferences2` geri çağırma sırasında geçerli değildir çünkü çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabilir. Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `RootReferences2` . [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
