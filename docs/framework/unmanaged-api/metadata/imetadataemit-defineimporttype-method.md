---
title: IMetaDataEmit::DefineImportType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 94ce4443be210fdfeb1bab197c3e603255e1cc4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723252"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType Yöntemi

Geçerli kapsamın dışında tanımlanan belirtilen türe bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pAssemImport`  
 'ndaki Hedef türün içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) arabirimi.  
  
 `pbHashValue`  
 'ndaki Tarafından belirtilen derlemenin karmasını içeren bir dizi `pAssemImport` .  
  
 `cbHashValue`  
 'ndaki Dizideki bayt sayısı `pbHashValue` .  
  
 `pImport`  
 'ndaki Hedef türün içeri aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) arabirimi.  
  
 `tdImport`  
 'ndaki `mdTypeDef` Hedef türünü belirten bir belirteç.  
  
 `pAssemEmit`  
 'ndaki Hedef türün içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) arabirimi.  
  
 `ptr`  
 dışı `mdTypeRef` Tür başvurusu için geçerli kapsamda tanımlanan belirteç.  
  
## <a name="remarks"></a>Açıklamalar  

 [Imetadatayay::D Efineımportmember](imetadataemit-defineimportmember-method.md) metodunu çağırmadan önce, `DefineImportType` üyenin üst sınıfı veya üst arabirimi için geçerli kapsamda bir tür başvurusu oluşturmak için yöntemini kullanabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
