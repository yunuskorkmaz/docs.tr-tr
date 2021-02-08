---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineProperty yöntemi'
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
ms.openlocfilehash: c0c0b6009f8674a5edebf1c982e277f4ca5b185b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784041"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty Yöntemi

Belirtilen ve Yöntem erişimcilerine sahip olan belirtilen tür için bir özellik tanımı oluşturur `get` `set` ve bu özellik tanımına bir belirteç alır.  
  
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
 'ndaki İçindeki bayt sayısı `pvSig` .  
  
 `dwCPlusTypeFlag`  
 'ndaki Özelliğin varsayılan değerinin türü.  
  
 `pValue`  
 'ndaki Özelliğin varsayılan değeri.  
  
 `cchValue`  
 'ndaki İçindeki (Unicode) karakterlerin sayısı `pValue` .  
  
 `mdSetter`  
 'ndaki Özellik değerini ayarlayan yöntem.  
  
 `mdGetter`  
 'ndaki Özellik değerini alan yöntem.  
  
 `rmdOtherMethods[]`  
 'ndaki Özelliği ile ilişkili diğer yöntemlerin dizisi. Diziyi bir ile sonlandırın `mdTokenNil` .  
  
 `pmdProp`  
 dışı `mdProperty` Atanan belirteç.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
