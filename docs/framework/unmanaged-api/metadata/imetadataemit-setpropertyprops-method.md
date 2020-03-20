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
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177471"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps Yöntemi
[DefineProperty Yöntemi'ne](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)önceki bir çağrıyla tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar.  
  
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
 [içinde] Özelliğin değiştirilecek belirteci  
  
 `dwPropFlags`  
 [içinde] Özellik bayrakları.  
  
 `dwCPlusTypeFlag`  
 [içinde] Özelliğin varsayılan değerinin türü.  
  
 `pValue`  
 [içinde] Özellik için varsayılan değer.  
  
 `cchValue`  
 [içinde] (Unicode) karakter `pValue`sayısı.  
  
 `mdSetter`  
 [içinde] Özellik değerini ayarlayan yöntem.  
  
 `mdGetter`  
 [içinde] Özellik değerini alan yöntem.  
  
 `rmdOtherMethods[]`  
 [içinde] Özellik ile ilişkili diğer yöntemler dizisi. Bu diziyi `mdTokenNil` bir belirteçle sonlandırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
