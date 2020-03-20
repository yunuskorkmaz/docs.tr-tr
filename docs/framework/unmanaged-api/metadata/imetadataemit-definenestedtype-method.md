---
title: IMetaDataEmit::DefineNestedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175817"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType Yöntemi
Bir tür tanımının meta veri imzasını `mdTypeDef` oluşturur, bu tür için bir belirteç döndürür ve tanımlanan `tdEncloser` türün parametre tarafından başvurulan türe üye olduğunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szTypeDef`  
 [içinde] Unicode'daki türün adı.  
  
 `dwTypeDefFlags`  
 [içinde] `TypeDef` öznitelikleri. Bu `CorTypeAttr` değerlerin bir bitmask olduğunu.  
  
 `tkExtends`  
 [içinde] Taban sınıfın belirteci. Bu ya `mdTypeDef` bir `mdTypeRef` ya da bir belirteç.  
  
 `rtkImplements`[]  
 [içinde] Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten belirteçler dizisi.  
  
 `tdEncloser`  
 [içinde] Çevreleyen türün belirteci. Dizinin son öğesi `mdTokenNil`.  
  
 `ptd`  
 [çıkış] Atanan `mdTypeDef` belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
