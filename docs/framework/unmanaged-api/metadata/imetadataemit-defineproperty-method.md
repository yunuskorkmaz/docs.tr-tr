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
ms.openlocfilehash: f11b374ed0ecbfc137c43fb641ae691237604691
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431522"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty Yöntemi
Belirtilen `get` ve `set` yöntemi erişimcilerine sahip bir özellik tanımı oluşturur ve bu özellik tanımına bir belirteç alır.  
  
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
 'ndaki Üzerinde özelliğin tanımlandığı sınıf veya arabirim için belirteç.  
  
 `szProperty`  
 'ndaki Özelliğin adı.  
  
 `dwPropFlags`  
 'ndaki Özellik bayrakları.  
  
 `pvSig`  
 'ndaki Özellik imzası.  
  
 `cbSig`  
 'ndaki `pvSig`bayt sayısı.  
  
 `dwCPlusTypeFlag`  
 'ndaki Özelliğin varsayılan değerinin türü.  
  
 `pValue`  
 'ndaki Özelliğin varsayılan değeri.  
  
 `cchValue`  
 'ndaki `pValue`içindeki (Unicode) karakterlerin sayısı.  
  
 `mdSetter`  
 'ndaki Özellik değerini ayarlayan yöntem.  
  
 `mdGetter`  
 'ndaki Özellik değerini alan yöntem.  
  
 `rmdOtherMethods[]`  
 'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi. Diziyi bir `mdTokenNil`sonlandırın.  
  
 `pmdProp`  
 dışı `mdProperty` belirteci atandı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
