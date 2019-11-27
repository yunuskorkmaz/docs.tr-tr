---
title: IMetaDataEmit::SetPropertyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: 0fdec87324d6efa0f911e37573093c19b93c0349
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440541"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps Yöntemi
[DefineProperty metoduna](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)önceki bir çağrı tarafından tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pr`  
 'ndaki Değiştirilecek özelliğin belirteci  
  
 `dwPropFlags`  
 'ndaki Özellik bayrakları.  
  
 `dwCPlusTypeFlag`  
 'ndaki Özelliğin varsayılan değerinin türü.  
  
 `pValue`  
 'ndaki Özelliğin varsayılan değeri.  
  
 `cchValue`  
 'ndaki `pValue`içindeki (Unicode) karakterlerin sayısı.  
  
 `mdSetter`  
 'ndaki Özellik değerini ayarlayan yöntem.  
  
 `mdGetter`  
 'ndaki Özellik değerini alan yöntem.  
  
 `rmdOtherMethods[]`  
 'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi. Bu diziyi `mdTokenNil` bir belirteçle sonlandırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
