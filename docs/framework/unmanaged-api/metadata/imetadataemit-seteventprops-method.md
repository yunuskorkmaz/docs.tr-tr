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
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450323"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps Yöntemi
[Imetadatayayma::D efineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)için önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki Olay bayrakları. Bu, `CorEventAttr` değerlerinin bir bit dır.  
  
 `tkEventType`  
 'ndaki Olay sınıfı için belirteç. Bu bir `mdTypeDef` ya da `mdTypeRef` belirteci.  
  
 `mdAddOn`  
 'ndaki Olaya abone olmak için kullanılan yöntem veya null.  
  
 `mdRemoveOn`  
 'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.  
  
 `mdFire`  
 'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).  
  
 `rmdOtherMethods[]`  
 'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi. Dizinin son öğesi `mdMethodDefNil`olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
