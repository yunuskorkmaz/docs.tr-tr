---
title: "ICorProfilerCallback2::RootReferences2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29a5a3051b75df18a08498369aa5707a53caf75f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 Yöntemi
Çöp toplama gerçekleştikten sonra Profil Oluşturucu kök başvurular hakkında uyarır. Bu yöntem uzantısıdır [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 [in] Öğe sayısı `rootRefIds`, `rootKinds`, `rootFlags`, ve `rootIds` dizileri.  
  
 `rootRefIds`  
 [in] Nesne kimlikleri, her biri bir statik nesnesinin ya da nesneyi yığında başvuruda bulunan bir dizi. Öğeleri `rootKinds` dizi karşılık gelen öğelerinde sınıflandırmak için bilgiler sağlar `rootRefIds` dizi.  
  
 `rootKinds`  
 [in] Bir dizi [cor_prf_gc_root_kınd](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) atık toplama kök türünü gösteren değerler.  
  
 `rootFlags`  
 [in] Bir dizi [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) bir atık toplama kök özelliklerini açıklayan değerleri.  
  
 `rootIds`  
 [in] Çöp toplama kök değerine bağlı olarak ilgili ek bilgileri içeren bir tamsayı o noktaya UINT_PTR dizisi değerleri `rootKinds` parametresi.  
  
 Kök türü bir yığın ise, kök değişkenini içeren işlevi için kimliğidir. Bu kök kimliği 0 ise, CLR iç bir adlandırılmamış işlevi işlevdir. Kök türü bir tanıtıcı ise, kök atık toplama tanıtıcısını kimliğidir. Diğer kök türleri kimliği belirsiz bir değerdir ve yoksayılmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `rootRefIds`, `rootKinds`, `rootFlags`, Ve `rootIds` paralel diziler dizidir. Diğer bir deyişle, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, ve `rootIds[i]` tüm aynı kök ilgilendiren.  
  
 Her ikisi de `RootReferences` ve `RootReferences2` profil oluşturucu bildirmek için çağrılır. Profil oluşturucular normalde uygulamak bir yöntemi veya diğer, ancak ikisini birlikte, bilgilerin geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.  
  
 Girdileri mümkündür `rootRefIds` karşılık gelen kök başvurusu null ve yönetilen yığında bir nesneye başvurmuyor anlamına gelir. sıfır olmalıdır.  
  
 Tarafından döndürülen nesne kimlikleri `RootReferences2` çöp toplama nesneleri eski adreslerinden yeni adreslere taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerli değildir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `RootReferences2` çağırın. Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesneleri yeni konumlarına taşınır ve güvenli bir şekilde Denetlenmekte.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
