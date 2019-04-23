---
title: ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f5d2c08abbcab6bc1a6d0569b8e70d7c919def
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195871"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi
En son çöp toplamadan beri oluşturulan her belirtilen sınıf örneklerini sayısı hakkında daha fazla profil oluşturucu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cClassCount`  
 [in] Boyutu `classIds` ve `cObjects` dizileri.  
  
 `classIds`  
 [in] Bir dizi sınıfının kimlikleri, burada her kimliği ile bir veya daha fazla örneğini bir sınıfı belirtir.  
  
 `cObjects`  
 [in] Burada her tamsayı karşılık gelen sınıf için örnek sayısını belirtir, tamsayı dizisi `classIds` dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `classIds` Ve `cObjects` paralel diziler dizilerdir. Örneğin, `classIds[i]` ve `cObjects[i]` başvuru aynı sınıfı. Sınıfı, önceki çöp toplama işleminden itibaren hiçbir bir sınıf örneği oluşturulmuşsa atlanır. `ObjectsAllocatedByClass` Geri çağırma büyük nesne yığınında nesneleri bildirmez.  
  
 Sayıları tarafından bildirilen `ObjectsAllocatedByClass` yalnızca biriminizdeki tahmini fiyatlardır. Tam sayıları için kullanmak [Icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 `classIds` Varsa, dizi bir veya daha fazla null girişler içeriyor olabilir karşılık gelen `cObjects` dizi kaldırma tür vardır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
