---
title: 'ICorProfilerInfo7:: ApplyMetaData yöntemi'
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
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861703"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7:: ApplyMetaData yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 `IMetadataEmit::Define*` yöntemleri tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 'ndaki Meta verileri değişmiş olan modülün tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veri değişiklikleri [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından sonra yapılmışsa, yeni meta verileri kullanmadan önce bu yöntemi çağırmanız gerekir.  
  
 `ApplyMetaData` yalnızca aşağıdaki meta veri türlerinin eklenmesini destekler:  
  
- [IMetaDataAssemblyEmit::D efineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)öğesini çağırarak oluşturduğunuz kayıtları `AssemblyRef`. yöntemidir.  
  
- [ımetadatayayma::D efineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metodunu çağırarak oluşturduğunuz kayıtları `TypeRef`.  
  
- [ımetadatayay:: GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metodunu çağırarak oluşturduğunuz kayıtları `TypeSpec`.  
  
- [ımetadatayayma::D efineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metodunu çağırarak oluşturduğunuz kayıtları `MemberRef`.  
  
- [IMetaDataEmit2::D efineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metodunu çağırarak oluşturduğunuz kayıtları `MemberSpec`.  
  
- [ımetadatayayma::D efineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metodunu çağırarak oluşturduğunuz kayıtları `UserString`.  

.NET Core 3,0 ile başlayarak `ApplyMetaData`, aşağıdaki türleri de destekler:

- [ımetadatayayma::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemini çağırarak oluşturduğunuz kayıtları `TypeDef`.

- [ımetadatayayma::D efineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) metodunu çağırarak oluşturduğunuz kayıtları `MethodDef`. Ancak, var olan bir türe sanal yöntemler eklemek desteklenmez. Sanal yöntemler [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından önce eklenmelidir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](icorprofilerinfo7-interface.md)
