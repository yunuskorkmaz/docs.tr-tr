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
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503821"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam Yöntemi
Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `mdTypeDef` `mdMethodDef` Genel parametre tanımlamak için yöntemi veya oluşturucuyu temsil eden bir veya belirteci.  
  
 `ulParamSeq`  
 'ndaki Genel parametrenin dizini.  
  
 `dwParamFlags`  
 'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri.  
  
 `szname`  
 'ndaki Parametrenin adı.  
  
 `reserved`  
 'ndaki Bu parametre gelecekteki genişletilebilirlik için ayrılmıştır.  
  
 `rtkConstraints`  
 'ndaki Tür kısıtlamaları sıfır ile sonlandırılmış dizi. Dizi üyeleri bir `mdTypeDef` , `mdTypeRef` veya `mdTypeSpec` meta veri belirteci olmalıdır.  
  
 `pgp`  
 dışı Genel parametreyi temsil eden bir belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
