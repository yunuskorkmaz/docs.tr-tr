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
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007786"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps Yöntemi
[DefineProperty metoduna](imetadataemit-defineproperty-method.md)önceki bir çağrı tarafından tanımlanan bir özellik için meta verilerde depolanan özellikleri ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki İçindeki (Unicode) karakterlerin sayısı `pValue` .  
  
 `mdSetter`  
 'ndaki Özellik değerini ayarlayan yöntem.  
  
 `mdGetter`  
 'ndaki Özellik değerini alan yöntem.  
  
 `rmdOtherMethods[]`  
 'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi. Bu diziyi bir belirteçle sonlandırın `mdTokenNil` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
