---
title: IMetaDataEmit::DefineField Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8ba8a762c56a666c67b25b9ce0420099fce419a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223530"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField Yöntemi
Belirtilen meta verileri imza ile bir alan için bir tanım oluşturur ve bu alan tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [in] `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.  
  
 `szName`  
 [in] Unicode alan adı.  
  
 `dwFieldFlags`  
 [in] Alan öznitelikleri. Bu, bir bit maskesi, `CorFieldAttr` değerleri.  
  
 `pvSigBlob`  
 [in] Bir BLOB olarak alan imzası.  
  
 `cbSigBlob`  
 [in] Bayt sayısı `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** Sabit değer. Bu bir `CorElementType` değeri. Alan için sabit bir değer tanımlamayarak kullanırsanız `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] Alan için sabit bir değer.  
  
 `cchValue`  
 [in] \(Unicode) karakter cinsinden boyutu `pValue`.  
  
 `pmd`  
 [out] `mdFieldDef` Atanan simgesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
