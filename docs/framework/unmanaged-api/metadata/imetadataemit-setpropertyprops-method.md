---
title: IMetaDataEmit::SetPropertyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e78c4d7319a931ca7090d6f99651bc9660e4af8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782046"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps Yöntemi
Önceki bir çağrı tarafından tanımlanan bir özellik için meta verileri içinde depolanan özellikleri ayarlar [DefineProperty yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pr`  
 [in] Değiştirilecek özellik için belirteç  
  
 `dwPropFlags`  
 [in] Özellik bayrakları.  
  
 `dwCPlusTypeFlag`  
 [in] Özelliğin varsayılan değeri türü.  
  
 `pValue`  
 [in] Bir özellik için varsayılan değeri.  
  
 `cchValue`  
 [in] \(Unicode) sayısını karakterleri `pValue`.  
  
 `mdSetter`  
 [in] Özellik değeri ayarlar yönteminin.  
  
 `mdGetter`  
 [in] Yöntem özellik değerini alır.  
  
 `rmdOtherMethods[]`  
 [in] Özellikle ilişkili diğer yöntemleri dizisi. Bu dizi ile sonlandırmak bir `mdTokenNil` belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
