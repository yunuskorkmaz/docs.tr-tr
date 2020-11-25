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
ms.openlocfilehash: 80d33da2eb2a7f0cfbe5dcb7279fff9973dada2e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712930"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope Yöntemi

Bir derlemeyi geçerli kapsama aktarır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
 'ndaki İçeri aktarma derlemesi için arabirim (imzanın tanımlandığı yer).  
  
 `pbHashValue`  
 'ndaki Derlemenin karma blobu.  
  
 `cbHashValue`  
 'ndaki İçindeki bayt sayısı `pbHashValue` .  
  
 `import`  
 'ndaki İçeri aktarma meta veri kapsamı için arabirim.  
  
 `pbSigBlob`  
 'ndaki İçeri aktarılacak imza.  
  
 `cbSigBlob`  
 'ndaki Bayt cinsinden boyutu `pbSigBlob` .  
  
 `pAssemEmit`  
 'ndaki Dışarı aktarma derlemesi için arabirim.  
  
 `emit`  
 'ndaki Dışarı aktarma meta verileri kapsamı için arabirim.  
  
 `pvTranslatedSig`  
 dışı Çevrilen imza blobunu tutan arabellek.  
  
 `cbTranslatedSigMax`  
 'ndaki Öğesinin bayt cinsinden kapasitesi `pvTranslatedSig` .  
  
 `pcbTranslatedSig`  
 dışı Çevrilen İmzadaki gerçek bayt sayısı.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
