---
title: IMetaDataEmit::SetFieldProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177549"
---
# <a name="imetadataemitsetfieldprops-method"></a>IMetaDataEmit::SetFieldProps Yöntemi
Belirtilen alan belirteci tarafından başvurulan alanın varsayılan değerini ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fd`  
 [içinde] Hedef alanın belirteci.  
  
 `dwFieldFlags`  
 [içinde] Alan öznitelikleri. Bu `CorFieldAttr` değerlerin bir bitmask olduğunu.  
  
 `dwCPlusTypeFlag`  
 [içinde] Sabit `ELEMENT_TYPE_` *\** değer için. Bu bir `CorElementType` değerdir. Bir sabit tanımlanmıyorsa, bu `ELEMENT_TYPE_END`değeri .  
  
 `pValue`  
 [içinde] Alan için sabit değer.  
  
 `cchValue`  
 [içinde] Unicode karakterlerinin boyutu. `pValue`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
