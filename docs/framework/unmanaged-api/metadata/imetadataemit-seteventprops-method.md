---
title: IMetaDataEmit::SetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008761"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps Yöntemi
[Imetadatayayma::D efineEvent](imetadataemit-defineevent-method.md)için önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ev`  
 'ndaki Olay belirteci.  
  
 `dwEventFlags`  
 'ndaki Olay bayrakları. Bu bir değer bit değeridir `CorEventAttr` .  
  
 `tkEventType`  
 'ndaki Olay sınıfı için belirteç. Bu bir ya da `mdTypeDef` bir `mdTypeRef` belirteç.  
  
 `mdAddOn`  
 'ndaki Olaya abone olmak için kullanılan yöntem veya null.  
  
 `mdRemoveOn`  
 'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.  
  
 `mdFire`  
 'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).  
  
 `rmdOtherMethods[]`  
 'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi. Dizinin son öğesi olmalıdır `mdMethodDefNil` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
