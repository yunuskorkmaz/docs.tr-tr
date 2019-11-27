---
title: IMetaDataEmit2::DefineGenericParam Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 3898b095809e2b84f71aba2036f4d7a294dfdf6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444658"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam Yöntemi
Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 'ndaki Genel parametre tanımlanacak yöntemi veya oluşturucuyu temsil eden bir `mdTypeDef` veya `mdMethodDef` belirteci.  
  
 `ulParamSeq`  
 'ndaki Genel parametrenin dizini.  
  
 `dwParamFlags`  
 'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) numaralandırması değeri.  
  
 `szname`  
 'ndaki Parametrenin adı.  
  
 `reserved`  
 'ndaki Bu parametre gelecekteki genişletilebilirlik için ayrılmıştır.  
  
 `rtkConstraints`  
 'ndaki Tür kısıtlamaları sıfır ile sonlandırılmış dizi. Dizi üyeleri bir `mdTypeDef`, `mdTypeRef`veya `mdTypeSpec` meta veri belirteci olmalıdır.  
  
 `pgp`  
 dışı Genel parametreyi temsil eden bir belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
