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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9debf041a26af128dea3cde214630f5a95eac71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992543"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType Yöntemi
Geçerli kapsam dışında tanımlanan ve bu başvuru için bir belirteç tanımlar belirtilen türe başvuru oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Bir [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) içinden hedef türü alındığından derleme temsil eden arabirim.  
  
 `pbHashValue`  
 [in] Tarafından belirtilen derleme için karma içeren bir dizi `pAssemImport`.  
  
 `cbHashValue`  
 [in] Bayt sayısı `pbHashValue` dizisi.  
  
 `pImport`  
 [in] Bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) içinden hedef türü alındığından meta veri kapsamı temsil eden arabirim.  
  
 `tdImport`  
 [in] Bir `mdTypeDef` hedef türünü belirten bir belirteç.  
  
 `pAssemEmit`  
 [in] Bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) hedef türü alınan derleme temsil eden arabirim.  
  
 `ptr`  
 [out] `mdTypeRef` Tür başvurusu için geçerli kapsamda tanımlı belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrılmadan önce [Imetadataemit::defineımportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) yöntemi kullanabileceğiniz `DefineImportType` üyenin üst sınıfta veya üst arabirimi için geçerli kapsam içinde bir tür başvurusu oluşturmak için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
