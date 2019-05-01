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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09616243aef272be041573864effd25017cc65c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992036"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 Yöntemi
Bir çöp toplama işlemi gerçekleştirildikten sonra Profil Oluşturucu kök başvurular hakkında bilgilendirir. Bu yöntem bir uzantısıdır [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 [in] İçindeki öğelerin sayısını `rootRefIds`, `rootKinds`, `rootFlags`, ve `rootIds` dizileri.  
  
 `rootRefIds`  
 [in] Statik nesne veya bir nesne yığını üzerindeki her biri başvuran nesne kimlikleri, bir dizi. Öğeleri `rootKinds` dizisi karşılık gelen öğeleri sınıflandırmak için bilgi sağlayın `rootRefIds` dizisi.  
  
 `rootKinds`  
 [in] Bir dizi [cor_prf_gc_root_kınd](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) çöp toplama kök türünü gösteren değerleri.  
  
 `rootFlags`  
 [in] Bir dizi [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) bir çöp toplama kök özelliklerini açıklayan değerleri.  
  
 `rootIds`  
 [in] Bir dizi UINT_PTR o noktaya değerine bağlı olarak, atık toplama kök hakkında ek bilgi içeren bir tamsayı değerleri `rootKinds` parametresi.  
  
 Bir yığın kökünün türü ise kök değişken içeren işlevi kimliğidir. Bu kök kimliği 0 ise, CLR iç adlandırılmamış bir işlev işlevdir. Kök türü bir tanıtıcı ise kök çöp toplama tanıtıcılarını kimliğidir. Diğer kök türleri için kimliği belirsiz bir değerdir ve yoksayılacak.  
  
## <a name="remarks"></a>Açıklamalar  
 `rootRefIds`, `rootKinds`, `rootFlags`, Ve `rootIds` paralel diziler dizilerdir. Diğer bir deyişle, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, ve `rootIds[i]` tümü aynı kök ilgilendiriyor.  
  
 Her ikisi de `RootReferences` ve `RootReferences2` profil oluşturucu bildirmek için çağırılır. Profil oluşturucular tarafından normalde uygulanır bir yöntem veya diğer, ikisi, bilgi geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.  
  
 Girdileri mümkündür `rootRefIds` , karşılık gelen kök başvuru null ve yönetilen yığındaki bir nesneye başvurmuyor anlamına gelir ve sıfır olmalıdır.  
  
 Tarafından döndürülen nesne kimlikleri `RootReferences2` çöp toplama nesneleri eski adreslerinden yeni adreslerine taşıma ortasında olabileceğinden geri kendisini sırasında geçerli değildir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `RootReferences2` çağırın. Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesnelerin yeni konumlarına taşınır ve güvenli bir şekilde inceledi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
