---
title: ICorProfilerInfo7::ApplyMetaData yöntemi
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7fa8e2f06faa399734c44b1a52b41246296ef3f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498919"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7::ApplyMetaData yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]  
  
 Yeni tarafından tanımlanan meta veriler geçerli `IMetadataEmit::Define*` Belirtilen modül için yöntemleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] Modül, meta verileri değiştirildi tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonra meta verileri değişiklikler yapılırsa [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri yeni meta veriler kullanmadan önce bu yöntemini çağırmalıdır.  
  
 `ApplyMetaData` Yalnızca şu meta veri türleri eklemeyi destekler:  
  
-   `AssemblyRef` çağırarak denetlediği oluşturma records [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). yöntem.  
  
-   `TypeRef` çağırarak denetlediği oluşturma records [Imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) yöntemi.  
  
-   `TypeSpec` çağırarak denetlediği oluşturma records [Imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) yöntemi.  
  
-   `MemberRef` çağırarak denetlediği oluşturma records [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) yöntemi.  
  
-   `MemberSpec` çağırarak denetlediği oluşturma records [Imetadataemit2::definemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) yöntemi.  
  
-   `UserString` çağırarak denetlediği oluşturma records [Imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) yöntemi.  

.NET Core 3.0 ile başlayan `ApplyMetaData` ayrıca aşağıdaki türlerini destekler:

- `TypeDef` çağırarak denetlediği oluşturma records [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemi.

- `MethodDef` çağırarak denetlediği oluşturma records [Imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) yöntemi. Ancak, sanal yöntemleri mevcut türü için ekleme desteklenmiyor. Sanal yöntemler eklendi, önce [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
