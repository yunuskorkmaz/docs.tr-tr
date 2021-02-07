---
description: ': Imetadatayayma:: SetTypeDefProps Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1160d20e7ceb422390f8cd725a75fdb4f42318e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706506"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps Yöntemi

[Imetadatayay::D efinetypedef](imetadataemit-definetypedef-method.md)önceki çağrısıyla tanımlanan bir türün özelliklerini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki `mdTypeDef` Özgün [ımetadatayay](imetadataemit-definetypedef-method.md)çağrısından alınan bir belirteç::D efinetypedef.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` özelliklerine. Bu bir değer bit değeridir `CorTypeAttr` .  
  
 `tkExtends`  
 'ndaki `mdToken` Temel sınıfın. Imetadatayayma için önceki bir çağrıdan alındı [::D Efineımporttype](imetadataemit-defineimporttype-method.md)veya `null` .  
  
 `rtkImplements[]`  
 'ndaki Bu türün uyguladığı arabirimler için bir belirteç dizisi. Bu `mdTypeRef` belirteçler [ımetadatayayma::D Efineımporttype](imetadataemit-defineimporttype-method.md)kullanılarak elde edilir. Dizinin son öğesi olmalıdır `mdTokenNil` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
