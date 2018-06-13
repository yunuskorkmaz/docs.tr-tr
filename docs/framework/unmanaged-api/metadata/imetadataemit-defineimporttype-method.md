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
ms.openlocfilehash: 68e6f7599db55ed9429f159b380a8a9f8ae3f034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447492"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType Yöntemi
Geçerli kapsamı dışında tanımlanır ve bu başvurusu için bir belirteç tanımlayan belirtilen türüne bir başvuru oluşturur.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `pAssemImport`  
 [in] Bir [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , hedef türü alındığından derleme temsil eden arabirim.  
  
 `pbHashValue`  
 [in] Belirtilen derleme için karma içeren bir dizi `pAssemImport`.  
  
 `cbHashValue`  
 [in] Bayt sayısı `pbHashValue` dizi.  
  
 `pImport`  
 [in] Bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , hedef türü alındığından meta veri kapsamı temsil eden arabirim.  
  
 `tdImport`  
 [in] Bir `mdTypeDef` belirteci hedef türünü belirtir.  
  
 `pAssemEmit`  
 [in] Bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) içine hedef türü alındığından derleme temsil eden arabirim.  
  
 `ptr`  
 [out] `mdTypeRef` Tür başvurusu için geçerli kapsamda tanımlı belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrılmadan önce [Imetadataemit::defineımportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) kullanabileceğiniz yöntemi, `DefineImportType` üyenin üst sınıf veya üst arabirimi için geçerli kapsam içinde bir tür başvurusu oluşturmak için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
