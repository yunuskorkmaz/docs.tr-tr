---
title: ICorProfilerCallback::RootReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94b736a8e3250f4d208d4a9a46a022140b676318
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631371"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences Yöntemi
Profil oluşturucuyu çöp toplamadan sonra kök başvuruları hakkındaki bilgileri ile bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 [in] Başvuruları sayısını `rootRefIds` dizisi.  
  
 `rootRefIds`  
 [in] Statik nesne veya yığındaki bir nesne başvurusu nesne kimlikleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Her ikisi de `RootReferences` ve [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) profil oluşturucu bildirmek için çağırılır. Profil oluşturucular tarafından normalde uygulanır birini veya diğerini, ancak ikisi birden değil, bilgi geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.  
  
 Mümkündür `rootRefIds` dizisi null bir nesne içerir. Örneğin, yığın üzerinde bildirilen tüm nesne başvuruları kökleri çöp toplayıcısı tarafından kabul edilir ve her zaman bildirilir.  
  
 Tarafından döndürülen nesne kimlikleri `RootReferences` çöp toplama nesneleri eski adreslerinden yeni adreslerine taşıma ortasında olabileceğinden geri kendisini sırasında geçerli değildir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek kullanmamanız gerekir bir `RootReferences` çağırın. Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesnelerin yeni konumlarına taşınır ve güvenli bir şekilde inceledi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
