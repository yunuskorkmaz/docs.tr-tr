---
title: IMetaDataEmit::TranslateSigWithScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71029d6ebfb3248da791d4371dfe3e39589af443
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207649"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope Yöntemi
Bir derleme geçerli kapsam içeri aktarır ve yeni bir meta veri imzası birleştirilmiş kapsamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAssemImport`  
 [in] Arabirim (imza tanımlandığı) alma derleme için.  
  
 `pbHashValue`  
 [in] Derleme için karma blob.  
  
 `cbHashValue`  
 [in] Bayt sayısı `pbHashValue`.  
  
 `import`  
 [in] İçeri aktarma meta veri kapsamı için arabirim.  
  
 `pbSigBlob`  
 [in] İçeri aktarılacak imzası.  
  
 `cbSigBlob`  
 [in] Bayt cinsinden boyutu, `pbSigBlob`.  
  
 `pAssemEmit`  
 [in] Dışarı aktarma derleme için arabirim.  
  
 `emit`  
 [in] Dışarı aktarma meta veri kapsamı için arabirim.  
  
 `pvTranslatedSig`  
 [out] Çevrilmiş imzası blob tutan arabellek.  
  
 `cbTranslatedSigMax`  
 [in] Bayt cinsinden kapasite, `pvTranslatedSig`.  
  
 `pcbTranslatedSig`  
 [out] Çevrilmiş imzasında gerçek bayt sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
