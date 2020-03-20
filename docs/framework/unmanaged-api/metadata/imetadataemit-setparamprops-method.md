---
title: IMetaDataEmit::SetParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177502"
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps Yöntemi
[IMetaDataEmit::DefineParam'a](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)yapılan bir önceki çağrı yla tanımlanan yöntem parametresinin özelliklerini ayarlar veya değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pd`  
 [içinde] Hedef parametrenin belirteci.  
  
 `szName`  
 [içinde] Unicode'daki parametrenin adı.  
  
 `dwParamFlags`  
 [içinde] Parametre nin bayrakları.  
  
 `dwCPlusTypeFlag`  
 [içinde] Sabit değer için ELEMENT_TYPE_*.  
  
 `pValue`  
 [içinde] Parametrenin sabit değeri.  
  
 `cchValue`  
 [içinde] (Unicode) karakterlerinin `pValue`boyutu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
