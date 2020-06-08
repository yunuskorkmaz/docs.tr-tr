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
ms.openlocfilehash: c30206145d08a22af49c4a6a0dc83fd7382bcc06
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495516"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7:: ApplyMetaData yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Yöntemler tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular `IMetadataEmit::Define*` .  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
 `ApplyMetaData`yalnızca aşağıdaki meta veri türlerinin eklenmesini destekler:  
  
- `AssemblyRef`[IMetaDataAssemblyEmit::D efineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md)' i çağırarak oluşturduğunuz kayıtlar. yöntemidir.  
  
- `TypeRef`[ımetadatayay::D efineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.  
  
- `TypeSpec`[ımetadatayay:: GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.  
  
- `MemberRef`[ımetadatayay::D efineMemberRef](../metadata/imetadataemit-definememberref-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.  
  
- `MemberSpec`[IMetaDataEmit2::D efineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.  
  
- `UserString`[ımetadatayay::D efineUserString](../metadata/imetadataemit-defineuserstring-method.md) metodunu çağırarak oluşturduğunuz kayıtlar.  

.NET Core 3,0 ile başlayarak, `ApplyMetaData` aşağıdaki türleri de destekler:

- `TypeDef`[ımetadatayayma::D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) yöntemini çağırarak oluşturduğunuz kayıtlar.

- `MethodDef`[ımetadatayayma::D efineMethod](../metadata/imetadataemit-definemethod-method.md) metodunu çağırarak oluşturduğunuz kayıtlar. Ancak, var olan bir türe sanal yöntemler eklemek desteklenmez. Sanal yöntemler [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısından önce eklenmelidir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo7 Arabirimi](icorprofilerinfo7-interface.md)
