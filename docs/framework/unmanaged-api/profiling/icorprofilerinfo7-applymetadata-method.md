---
title: "ICorProfilerInfo7::ApplyMetaData yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e79d687d3d777895dea9427e4865c2fc866f50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7::ApplyMetaData yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]  
  
 Yeni tarafından tanımlanan meta verilerine uygulanır `IMetadataEmit::Define*` Belirtilen modül yöntemleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] Meta verileri değiştirildi modülü tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veri değişiklikleri sonra yapılırsa [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri arama, yeni meta kullanmadan önce bu yöntem çağırmalıdır.  
  
 `ApplyMetaData`Yalnızca şu meta veri türleri ekleme destekler:  
  
-   `AssemblyRef`çağırarak oluşturduğunuz kayıtları [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). yöntem.  
  
-   `TypeRef`çağırarak oluşturduğunuz kayıtları [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) yöntemi.  
  
-   `TypeSpec`çağırarak oluşturduğunuz kayıtları [Imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) yöntemi.  
  
-   `MemberRef`çağırarak oluşturduğunuz kayıtları [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) yöntemi.  
  
-   `MemberSpec`çağırarak oluşturduğunuz kayıtları [Imetadataemit2::definemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) yöntemi.  
  
-   `UserString`çağırarak oluşturduğunuz kayıtları [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
