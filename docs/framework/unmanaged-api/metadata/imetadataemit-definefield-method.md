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
ms.openlocfilehash: 2bc2b983171dc41d5ac37eda0359f1aaee4ebd6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725761"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField Yöntemi

Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
 'ndaki `mdTypeDef` Kapsayan sınıf veya arabirim için belirteç.  
  
 `szName`  
 'ndaki Unicode 'daki alan adı.  
  
 `dwFieldFlags`  
 'ndaki Alan öznitelikleri. Bu bir değer bit değeridir `CorFieldAttr` .  
  
 `pvSigBlob`  
 'ndaki BLOB olarak alan imzası.  
  
 `cbSigBlob`  
 'ndaki İçindeki bayt sayısı `pvSigBlob` .  
  
 `dwCPlusTypeFlag`  
 'ndaki `ELEMENT_TYPE_` *\** Sabit değer için. Bu bir `CorElementType` değerdir. Alan için sabit bir değer tanımlamadıysanız kullanın `ELEMENT_TYPE_END` .  
  
 `pValue`  
 'ndaki Alanın sabit değeri.  
  
 `cchValue`  
 'ndaki (Unicode) karakter boyutu `pValue` .  
  
 `pmd`  
 dışı `mdFieldDef` Atanan belirteç.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
