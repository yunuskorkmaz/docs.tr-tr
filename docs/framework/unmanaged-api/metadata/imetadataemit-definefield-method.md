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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177709"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField Yöntemi
Belirtilen meta veri imzasına sahip bir alan için tanım oluşturur ve bu alan tanımına bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [içinde] Çevreleyen `mdTypeDef` sınıf veya arabirim için belirteç.  
  
 `szName`  
 [içinde] Unicode'daki alan adı.  
  
 `dwFieldFlags`  
 [içinde] Alan öznitelikleri. Bu `CorFieldAttr` değerlerin bir bitmask olduğunu.  
  
 `pvSigBlob`  
 [içinde] BLOB olarak alan imzası.  
  
 `cbSigBlob`  
 [içinde] Bayt `pvSigBlob`sayısı.  
  
 `dwCPlusTypeFlag`  
 [içinde] Sabit `ELEMENT_TYPE_` *\** değer için. Bu bir `CorElementType` değerdir. Alan için sabit bir değer tanımlanmıyorsanız, kullanın. `ELEMENT_TYPE_END`  
  
 `pValue`  
 [içinde] Alan için sabit değer.  
  
 `cchValue`  
 [içinde] (Unicode) karakterlerinin `pValue`boyutu.  
  
 `pmd`  
 [çıkış] Atanan `mdFieldDef` belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
