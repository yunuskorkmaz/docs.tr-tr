---
description: ': Imetadatayayma:: TranslateSigWithScope yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e5f4e522e993f2f391ca0c29e5fcc2cbb71775e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720940"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope Yöntemi

Bir derlemeyi geçerli kapsama aktarır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
