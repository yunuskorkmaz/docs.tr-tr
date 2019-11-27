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
ms.openlocfilehash: dffd4365669da61f7b321110ad663c131ce591e6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439673"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 Yöntemi
Çöp toplama gerçekleştirildikten sonra profil oluşturucuyu kök başvuruları hakkında bilgilendirir. Bu yöntem [ICorProfilerCallback:: RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) yönteminin bir uzantısıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki `rootRefIds`, `rootKinds`, `rootFlags`ve `rootIds` dizilerindeki öğe sayısı.  
  
 `rootRefIds`  
 'ndaki Her biri bir statik nesneye veya yığında bir nesneye başvuran bir nesne kimlikleri dizisi. `rootKinds` dizisindeki öğeler, `rootRefIds` dizisinde karşılık gelen öğeleri sınıflandırmak için bilgi sağlar.  
  
 `rootKinds`  
 'ndaki Çöp toplama kökünün türünü belirten [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) değerleri dizisi.  
  
 `rootFlags`  
 'ndaki Bir çöp toplama kökünün özelliklerini tanımlayan [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) değerleri dizisi.  
  
 `rootIds`  
 'ndaki `rootKinds` parametresinin değerine bağlı olarak çöp toplama köküyle ilgili ek bilgiler içeren bir tamsayıyı işaret eden UINT_PTR değerleri dizisi.  
  
 Kök türü bir yığın ise, kök KIMLIĞI değişkeni içeren işleve yöneliktir. Bu kök KIMLIĞI 0 ise, işlev CLR 'ye iç olan adlandırılmamış bir işlevdir. Kök türü bir tanıtıcı ise, kök KIMLIĞI çöp toplama tutamacı içindir. Diğer kök türleri için KIMLIK donuk bir değerdir ve göz ardı edilmelidir.  
  
## <a name="remarks"></a>Açıklamalar  
 `rootRefIds`, `rootKinds`, `rootFlags`ve `rootIds` dizileri paralel dizilerdir. Diğer bir deyişle, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`ve `rootIds[i]` hepsi aynı köke sorun.  
  
 Profil oluşturucuyu bildirmek için hem `RootReferences` hem de `RootReferences2` çağırılır. Profil oluşturucular, genellikle bir yöntemi veya diğerini uygular, çünkü `RootReferences2` geçirilen bilgiler, `RootReferences`geçirilen bir üst kümesidir.  
  
 `rootRefIds` içindeki girişlerin sıfır olması mümkündür. Bu, karşılık gelen kök başvurusunun null olduğunu ve yönetilen yığında bir nesneye başvurmayacağı anlamına gelir.  
  
 Çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabileceğinden, `RootReferences2` tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir. Bu nedenle, profil oluşturucular `RootReferences2` çağrısı sırasında nesneleri incelemeyi denememelidir. [ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
