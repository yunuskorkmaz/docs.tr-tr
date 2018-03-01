---
title: "ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi"
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
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4adeda7ac884b37bcfc2b0c9599dd8e36c469747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi
Profil Oluşturucu en son çöp toplamadan beri oluşturulan her belirtilen sınıf örneklerini sayısı hakkında uyarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cClassCount`  
 [in] Boyutunu `classIds` ve `cObjects` dizileri.  
  
 `classIds`  
 [in] Bir dizi sınıfının kimlikleri, burada her kimliği ile bir veya daha fazla örnekleri bir sınıfı belirtir.  
  
 `cObjects`  
 [in] Dizisi burada her tamsayı belirtir, karşılık gelen sınıf için örnek sayısı, `classIds` dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `classIds` Ve `cObjects` paralel diziler dizidir. Örneğin, `classIds[i]` ve `cObjects[i]` aynı sınıf başvurusu. Bir sınıf örneği önceki çöp toplamadan beri oluşturulduysa sınıfı atlanır. `ObjectsAllocatedByClass` Geri çağırma büyük nesne yığın ayrılmış nesneleri bildirmez.  
  
 Sayıları tarafından bildirilen `ObjectsAllocatedByClass` yalnızca tahminleri. Tam sayılar için kullanmak [Icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 `classIds` Dizisi, bir veya daha fazla null girdiler içerebilir, varsa karşılık gelen `cObjects` dizi kaldırılması türü içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
