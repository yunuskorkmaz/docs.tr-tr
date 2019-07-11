---
title: ICorProfilerInfo2::GetObjectGeneration Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ab77b3e57213bd2c697dcb9222055b8d8f49210
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782277"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration Yöntemi
Belirtilen nesneyi içeren yığın kesimini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 [in] Nesnenin kimliği.  
  
 `range`  
 [out] Bir işaretçi bir [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapısı, bellek çeşitli (diğer bir deyişle, bir blok) içinde çöp toplama aşamasında oluşturmayı açıklar. Bu aralık, belirtilen nesne içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetObjectGeneration` Yöntemi çağrılabilir herhangi bir profil oluşturucu geri çağrısından koşuluyla atık toplama devam ederken değil. Diğer bir deyişle, herhangi bir geri çağırma arasında gerçekleşen hariç çağrılabilir [Icorprofilercallback2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ve [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
