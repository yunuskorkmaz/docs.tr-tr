---
title: IMetaDataEmit::SetTypeDefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007773"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps Yöntemi
[Imetadatayay::D efinetypedef](imetadataemit-definetypedef-method.md)önceki çağrısıyla tanımlanan bir türün özelliklerini ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki `mdTypeDef`Özgün [ımetadatayay](imetadataemit-definetypedef-method.md)çağrısından alınan bir belirteç::D efinetypedef.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` özelliklerine. Bu bir değer bit değeridir `CorTypeAttr` .  
  
 `tkExtends`  
 'ndaki `mdToken`Temel sınıfın. Imetadatayayma için önceki bir çağrıdan alındı [::D Efineımporttype](imetadataemit-defineimporttype-method.md)veya `null` .  
  
 `rtkImplements[]`  
 'ndaki Bu türün uyguladığı arabirimler için bir belirteç dizisi. Bu `mdTypeRef` belirteçler [ımetadatayayma::D Efineımporttype](imetadataemit-defineimporttype-method.md)kullanılarak elde edilir. Dizinin son öğesi olmalıdır `mdTokenNil` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
