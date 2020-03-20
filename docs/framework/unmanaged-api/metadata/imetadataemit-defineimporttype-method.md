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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177688"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType Yöntemi
Geçerli kapsam dışında tanımlanan belirtilen türe bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [içinde] Hedef türün içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyAlma](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.  
  
 `pbHashValue`  
 [içinde] Tarafından belirtilen derleme için karma içeren `pAssemImport`bir dizi.  
  
 `cbHashValue`  
 [içinde] Dizideki `pbHashValue` bayt sayısı.  
  
 `pImport`  
 [içinde] Hedef türün içe aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.  
  
 `tdImport`  
 [içinde] `mdTypeDef` Hedef türünü belirten bir belirteç.  
  
 `pAssemEmit`  
 [içinde] Hedef türün içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) arabirimi.  
  
 `ptr`  
 [çıkış] Tür `mdTypeRef` başvurusu için geçerli kapsamda tanımlanan belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) yöntemini aramadan önce, `DefineImportType` geçerli kapsamda, üyenin üst sınıfı veya üst arabirimi için bir tür başvurusu oluşturmak için yöntemi kullanabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
