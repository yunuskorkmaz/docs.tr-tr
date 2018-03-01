---
title: "ICorProfilerCallback::RootReferences Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd057538450deeb46a72178c725103e04a8dd126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
