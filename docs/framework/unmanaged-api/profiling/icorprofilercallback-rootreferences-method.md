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
ms.openlocfilehash: 467d065ab4d47e698c7043697ebe2ccf5f98a3cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452591"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences Yöntemi
Profil Oluşturucu çöp toplamadan sonra kök başvurular hakkındaki bilgilerle bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 [in] Başvuruları sayısı `rootRefIds` dizi.  
  
 `rootRefIds`  
 [in] Statik bir nesne veya yığında bir nesne başvuru nesnesi kimlikleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Her ikisi de `RootReferences` ve [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) profil oluşturucu bildirmek için çağrılır. Profil oluşturucular normalde uygulamak birini veya diğerini, ancak ikisi birden değil, bilgileri geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.  
  
 Mümkündür `rootRefIds` dizi null bir nesne içeriyor. Örneğin, yığında bildirilen tüm nesne başvuruları kökleri atık toplayıcısı tarafından kabul edilir ve her zaman bildirilir.  
  
 Tarafından döndürülen nesne kimlikleri `RootReferences` çöp toplama nesneleri eski adreslerinden yeni adreslere taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerli değildir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `RootReferences` çağırın. Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesneleri yeni konumlarına taşınır ve güvenli bir şekilde Denetlenmekte.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
