---
title: IMetaDataEmit::DefineTypeDef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175765"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef Yöntemi
Ortak bir dil çalışma zamanı türü için bir tür tanımı oluşturur ve bu tür tanımı için bir meta veri belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szTypeDef`  
 [içinde] Unicode'daki türün adı.  
  
 `dwTypeDefFlags`  
 [içinde] `TypeDef` öznitelikleri. Bu `CoreTypeAttr` değerlerin bir bitmask olduğunu.  
  
 `tkExtends`  
 [içinde] Taban sınıfın belirteci. Ya bir `mdTypeDef` belirteç `mdTypeRef` ya da bir belirteç olmalı.  
  
 `rtkImplements`  
 [içinde] Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir dizi belirteç.  
  
 `ptd`  
 [çıkış] Atanan `mdTypeDef` belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `dwTypeDefFlags` bayrak, oluşturulan türün ortak bir tür sistem başvuru türü (sınıf veya arabirim) veya ortak bir tür sistem değer türü olup olmadığını belirtir.  
  
 Sağlanan parametrelere bağlı olarak, bu yöntem, bir yan etki `mdInterfaceImpl` olarak, aynı zamanda bu tür tarafından devralınan veya uygulanan her arabirim için bir kayıt oluşturabilir. Ancak, bu yöntem bu `mdInterfaceImpl` belirteçlerin hiçbirini döndürmez. İstemci daha sonra bir `mdInterfaceImpl` belirteç eklemek veya `IMetaDataImport` değiştirmek isterse, bunları sayısallandırmak için arabirimi kullanmalıdır. `[default]` Arabirimin COM semantiklerini kullanmak istiyorsanız, varsayılan arabirimi ilk öğe olarak `rtkImplements`sağlamanız gerekir; sınıfa ayarlanan özel bir öznitelik, sınıfın varsayılan arabirimi olduğunu gösterir (bu her zaman sınıf için bildirilen ilk `mdInterfaceImpl` belirteç olarak kabul edilir).  
  
 `rtkImplements` Dizinin her öğesi bir `mdTypeDef` `mdTypeRef` veya belirteç tutar. Dizideki son öğe `mdTokenNil`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
