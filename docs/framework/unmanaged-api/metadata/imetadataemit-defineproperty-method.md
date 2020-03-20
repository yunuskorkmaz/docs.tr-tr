---
title: IMetaDataEmit::DefineProperty Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175791"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty Yöntemi
Belirtilen tür için, belirtilen `get` ve `set` yöntem etekleri ile bir özellik tanımı oluşturur ve bu özellik tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [içinde] Özelliğin tanımlandığı sınıf veya arabirim için belirteç.  
  
 `szProperty`  
 [içinde] Mülkün adı.  
  
 `dwPropFlags`  
 [içinde] Mülk bayrakları.  
  
 `pvSig`  
 [içinde] Mülk imzası.  
  
 `cbSig`  
 [içinde] Bayt `pvSig`sayısı.  
  
 `dwCPlusTypeFlag`  
 [içinde] Özelliğin varsayılan değerinin türü.  
  
 `pValue`  
 [içinde] Özellik için varsayılan değer.  
  
 `cchValue`  
 [içinde] (Unicode) karakter `pValue`sayısı.  
  
 `mdSetter`  
 [içinde] Özellik değerini ayarlayan yöntem.  
  
 `mdGetter`  
 [içinde] Özellik değerini alan yöntem.  
  
 `rmdOtherMethods[]`  
 [içinde] Özellik ile ilişkili diğer yöntemler dizisi. Diziyi bir `mdTokenNil`ile sonlandırın  
  
 `pmdProp`  
 [çıkış] Atanan `mdProperty` belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
